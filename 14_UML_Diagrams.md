# UML Diagrams

## 1. Use Case Diagram
*(Refer to document 13_Use_Cases.md for the comprehensive Use Case diagram).*

## 2. Activity Diagram
This diagram shows the dynamic flow of activities when a student applies for leave.

```mermaid
flowchart TD
    Start((Start)) --> Login[Student logs into portal]
    Login --> Fill[Student fills application form]
    Fill --> CheckMed{Leave Type == 'Medical'?}
    
    CheckMed -- Yes --> Enforce[Enforce Document Upload]
    Enforce --> Upload[Student uploads file]
    Upload --> Submit
    
    CheckMed -- No --> Submit[Student submits application]
    
    Submit --> Validate[System validates data]
    Validate --> Pass{Validation Pass?}
    
    Pass -- No --> Error[Show Error Message]
    Error --> Stop1((Stop))
    
    Pass -- Yes --> Save[Save to Database as 'Pending Faculty']
    Save --> EmailFac[Send Email to Faculty]
    EmailFac --> Review[Faculty reviews application]
    
    Review --> FacApprove{Faculty approves?}
    
    FacApprove -- No --> FacReject[Update status to 'Rejected']
    FacReject --> FinalEmail
    
    FacApprove -- Yes --> Duration{Leave Duration > 3 days?}
    
    Duration -- No --> FacApproveStatus[Update status to 'Approved']
    FacApproveStatus --> FinalEmail
    
    Duration -- Yes --> PendHOD[Update status to 'Pending HOD']
    PendHOD --> EmailHOD[Send Email to HOD]
    EmailHOD --> HODReview[HOD reviews application]
    HODReview --> HODApprove{HOD approves?}
    
    HODApprove -- Yes --> HODApproveStatus[Update status to 'Approved']
    HODApproveStatus --> FinalEmail
    
    HODApprove -- No --> HODReject[Update status to 'Rejected']
    HODReject --> FinalEmail
    
    FinalEmail[Send Final Email to Student] --> Stop2((Stop))
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
