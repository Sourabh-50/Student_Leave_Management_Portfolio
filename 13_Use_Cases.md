# Use Cases

## 1. Use Case Diagram (Mermaid)

```mermaid
flowchart LR
    %% Actors
    Student([Student])
    Faculty([Faculty])
    HOD([HOD])
    Admin([Admin])

    %% Use Cases
    subgraph System ["Student Leave Management System"]
        direction TB
        UC1([Login SSO])
        UC2([Submit Leave Request])
        UC3([Upload Medical Certificate])
        UC4([Cancel Request])
        UC5([Review & Approve Leave])
        UC6([Reject Leave])
        UC7([View Department Analytics])
        UC8([Export Master Report])
    end

    %% Connections
    Student --> UC1
    Student --> UC2
    Student --> UC3
    Student --> UC4

    Faculty --> UC1
    Faculty --> UC5
    Faculty --> UC6

    HOD --> UC1
    HOD --> UC5
    HOD --> UC6
    HOD --> UC7

    Admin --> UC1
    Admin --> UC8
```

## 2. Detailed Use Case Description

### Use Case 02: Submit Leave Request

| Attribute | Description |
| :--- | :--- |
| **Use Case ID** | UC-02 |
| **Use Case Name** | Submit Leave Request |
| **Primary Actor** | Student |
| **Preconditions** | 1. The Student is logged into the SLMS.<br>2. The Student has an active enrollment status in the SIS. |
| **Postconditions** | 1. A leave request is saved in the database with status 'Pending Faculty'.<br>2. An email is sent to the assigned Faculty. |
| **Main Success Flow** | 1. Student navigates to "New Leave Application".<br>2. Student selects 'Start Date' and 'End Date'.<br>3. System calculates total days (excluding weekends).<br>4. Student selects 'Leave Type' (e.g., Personal).<br>5. Student enters a 'Reason'.<br>6. Student clicks 'Submit'.<br>7. System validates inputs.<br>8. System saves the record and displays a success message. |
| **Alternative Flow (A1: Medical Leave)** | 4a. Student selects 'Leave Type' = 'Medical'.<br>4b. System makes the 'Upload Attachment' field mandatory.<br>4c. Student uploads a PDF certificate.<br>4d. Return to step 5. |
| **Exception Flow (E1: Invalid Dates)** | 7a. System detects 'End Date' is before 'Start Date'.<br>7b. System blocks submission and shows error: "End date must be after start date".<br>7c. Student corrects the dates.<br>7d. Return to step 6. |

### Use Case 05: Review & Approve Leave

| Attribute | Description |
| :--- | :--- |
| **Use Case ID** | UC-05 |
| **Use Case Name** | Review & Approve Leave |
| **Primary Actor** | Faculty (or HOD) |
| **Preconditions** | 1. The Approver is logged in.<br>2. There is at least one 'Pending' request in their queue. |
| **Postconditions** | 1. The request status is updated.<br>2. If <= 3 days, it is 'Fully Approved'. If > 3 days, it is 'Pending HOD'. |
| **Main Success Flow** | 1. Faculty navigates to Dashboard.<br>2. Faculty clicks on a pending request row.<br>3. System displays modal with student details, dates, reason, and past leave history.<br>4. Faculty clicks 'Approve'.<br>5. System checks duration.<br>6. System determines duration is <= 3 days.<br>7. System marks as 'Approved' and emails Student. |
| **Alternative Flow (A1: Route to HOD)** | 6a. System determines duration is > 3 days.<br>6b. System marks as 'Pending HOD'.<br>6c. System emails HOD for secondary approval. |
| **Alternative Flow (A2: Reject)** | 4a. Faculty clicks 'Reject'.<br>4b. System prompts for mandatory rejection reason.<br>4c. Faculty types reason and submits.<br>4d. System marks as 'Rejected' and emails Student. |
