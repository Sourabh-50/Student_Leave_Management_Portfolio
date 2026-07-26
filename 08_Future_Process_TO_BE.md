# Future Process (TO-BE)

## 1. Digital Workflow Explanation
The proposed TO-BE process eliminates paper entirely. 
1. The student logs into the SLMS portal and fills out a digital form.
2. The system automatically calculates routing based on business rules.
3. The Faculty receives an email notification, logs in, reviews the student's digital history, and clicks 'Approve'.
4. If the leave is >3 days, the system automatically forwards it to the HOD's digital queue.
5. Once fully approved, the system updates the database, notifying both the Admin and the Student simultaneously. 

This process reduces turnaround time to under 24 hours and provides 100% transparency.

## 2. Workflow Diagram (Mermaid)

```mermaid
graph TD
    Start((Start)) --> A[Student logs into SLMS Portal]
    A --> B[Fills digital leave form & uploads proof]
    B --> C[Clicks Submit]
    C --> D{System Logic: Duration?}
    
    D -- "<= 3 Days" --> E[Route to Faculty Dashboard]
    D -- "> 3 Days" --> F[Route to Faculty, then HOD]
    
    E --> G[Faculty Reviews Request]
    F --> G
    
    G --> H{Faculty Decision}
    H -- Reject --> I[Add Comments & Reject]
    I --> J[System sends Rejection Email to Student] --> End1((End))
    
    H -- Approve --> K{Needs HOD Approval?}
    K -- No --> L[System updates status to 'Approved']
    
    K -- Yes --> M[Route to HOD Dashboard]
    M --> N[HOD Reviews Request]
    N --> O{HOD Decision}
    O -- Reject --> I
    O -- Approve --> L
    
    L --> P[System syncs data with Attendance Database]
    P --> Q[System sends Approval Email to Student]
    Q --> End2((End Process))
```

## 3. Notification & Approval Flow (Sequence Diagram)

```mermaid
sequenceDiagram
    autonumber
    participant Student
    participant System
    participant Faculty
    participant HOD
    participant Database
    
    Student->>System: Submit Digital Request (e.g., 4 Days)
    System->>Database: Save Request Status: 'Pending Faculty'
    System-->>Faculty: Trigger Email: "Action Required"
    
    Faculty->>System: Login & View Dashboard
    Faculty->>System: Click 'Approve'
    
    System->>Database: Update Status: 'Pending HOD' (due to >3 days rule)
    System-->>HOD: Trigger Email: "Action Required"
    
    HOD->>System: Login & View Dashboard
    HOD->>System: Click 'Approve'
    
    System->>Database: Update Status: 'Fully Approved'
    System-->>Student: Trigger Email: "Leave Approved"
```
