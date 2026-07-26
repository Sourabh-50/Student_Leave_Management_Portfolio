# Current Process (AS-IS)

## 1. Process Explanation
The existing leave management process is entirely physical and involves multiple manual hand-offs. 
1. The student collects a blank form from the admin office.
2. The student fills it out and attaches physical proof (if needed).
3. The student tracks down their Class Faculty for a signature. 
4. If the leave is greater than 3 days, they must then track down the HOD.
5. Once signed, the student submits the physical paper back to the Admin office.
6. The Admin manually enters the data into the attendance ledger.

This process takes an average of 3 to 5 days, creates frustration, and often results in lost paperwork.

## 2. BPMN Diagram (Mermaid)
*Note: Using Mermaid Flowchart to represent the BPMN structure.*

```mermaid
graph TD
    Start((Start)) --> A[Student gets blank paper form from Admin]
    A --> B[Student fills form & attaches proof]
    B --> C{Find Faculty?}
    C -- No --> D[Wait and try again later]
    D --> C
    C -- Yes --> E[Submit form to Faculty]
    E --> F[Faculty Reviews]
    F --> G{Approved?}
    G -- No --> H[Form returned to student] --> End1((End))
    G -- Yes --> I[Faculty signs form]
    I --> J{Leave > 3 Days?}
    J -- Yes --> K[Student takes form to HOD]
    K --> L[HOD Reviews and Signs]
    L --> M
    J -- No --> M[Student submits signed form to Admin]
    M --> N[Admin manually enters data into ledger]
    N --> O[Paper form archived in filing cabinet]
    O --> End2((End Process))
```

## 3. Swimlane Diagram (Mermaid)

```mermaid
sequenceDiagram
    participant Student
    participant Faculty
    participant HOD
    participant Admin
    
    Note over Student,Admin: Manual AS-IS Process
    
    Student->>Admin: Request blank leave form
    Admin-->>Student: Provide paper form
    Student->>Student: Fill details & attach medical proof
    Student->>Faculty: Physically submit form
    
    alt Leave is 1-3 Days
        Faculty->>Faculty: Review & Sign
        Faculty-->>Student: Return signed form
    else Leave is > 3 Days
        Faculty->>Faculty: Review & Sign
        Faculty-->>Student: Return signed form
        Student->>HOD: Physically submit form to HOD
        HOD->>HOD: Review & Sign
        HOD-->>Student: Return signed form
    end
    
    Student->>Admin: Submit fully approved form
    Admin->>Admin: Manually update attendance ledger
    Admin->>Admin: Store paper in physical file
```
