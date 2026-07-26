# UML Diagrams

## 1. Use Case Diagram
*(Refer to document 13_Use_Cases.md for the comprehensive Use Case diagram).*

## 2. Activity Diagram
This diagram shows the dynamic flow of activities when a student applies for leave.

```mermaid
activityDiagram
    start
    :Student logs into portal;
    :Student fills application form;
    if (Leave Type == 'Medical'?) then (Yes)
        :Enforce Document Upload;
        :Student uploads file;
    else (No)
    endif
    :Student submits application;
    :System validates data;
    if (Validation Pass?) then (Yes)
        :Save to Database as 'Pending Faculty';
        :Send Email to Faculty;
    else (No)
        :Show Error Message;
        stop
    endif
    
    :Faculty reviews application;
    if (Faculty approves?) then (Yes)
        if (Leave Duration > 3 days?) then (Yes)
            :Update status to 'Pending HOD';
            :Send Email to HOD;
            :HOD reviews application;
            if (HOD approves?) then (Yes)
                :Update status to 'Approved';
            else (No)
                :Update status to 'Rejected';
            endif
        else (No)
            :Update status to 'Approved';
        endif
    else (No)
        :Update status to 'Rejected';
    endif
    
    :Send Final Email to Student;
    stop
```

## 3. Sequence Diagram
This diagram shows the object interactions for the Faculty approval process.

```mermaid
sequenceDiagram
    actor Faculty
    participant UI as Web Interface
    participant API as Backend Server
    participant DB as PostgreSQL
    participant Email as SMTP Service

    Faculty->>UI: Click 'Approve' on Request #102
    UI->>API: POST /api/leaves/102/approve
    API->>DB: SELECT duration FROM leaves WHERE id=102
    DB-->>API: returns duration = 2
    
    alt duration <= 3
        API->>DB: UPDATE status = 'Approved'
        API->>Email: SEND approval_email to Student
        Email-->>API: 200 OK
        API-->>UI: 200 OK (Status Updated)
        UI-->>Faculty: Show Success Notification
    else duration > 3
        API->>DB: UPDATE status = 'Pending HOD'
        API->>Email: SEND action_required to HOD
        Email-->>API: 200 OK
        API-->>UI: 200 OK (Forwarded)
        UI-->>Faculty: Show Forwarded Notification
    end
```

## 4. Class Diagram
This represents the static structural data model of the system.

```mermaid
classDiagram
    class User {
        +UUID id
        +String name
        +String email
        +String role
        +login()
        +logout()
    }
    class Student {
        +String rollNumber
        +String department
        +Float attendancePercentage
        +submitLeave()
    }
    class Faculty {
        +String department
        +approveLeave()
        +rejectLeave()
    }
    class LeaveRequest {
        +UUID request_id
        +Date startDate
        +Date endDate
        +Int totalDays
        +String leaveType
        +String reason
        +String attachmentUrl
        +String status
        +String approverComments
    }
    
    User <|-- Student
    User <|-- Faculty
    Student "1" -- "0..*" LeaveRequest : creates
    Faculty "1" -- "0..*" LeaveRequest : reviews
```

## 5. State Machine Diagram
This diagram outlines the lifecycle states of a single `LeaveRequest` object.

```mermaid
stateDiagram-v2
    [*] --> Draft : Student starts form
    Draft --> Pending_Faculty : Student submits
    
    Pending_Faculty --> Cancelled : Student cancels
    Pending_Faculty --> Rejected : Faculty Rejects
    
    Pending_Faculty --> Approved : Faculty Approves (<=3 Days)
    Pending_Faculty --> Pending_HOD : Faculty Approves (>3 Days)
    
    Pending_HOD --> Rejected : HOD Rejects
    Pending_HOD --> Approved : HOD Approves
    
    Cancelled --> [*]
    Rejected --> [*]
    Approved --> [*]
```
