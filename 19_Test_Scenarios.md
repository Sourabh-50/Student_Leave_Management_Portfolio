# Test Scenarios (UAT & Functional)

This document outlines the critical testing scenarios necessary to ensure the SLMS meets business requirements before Go-Live.

## 1. Functional Testing

### 1.1 Positive Scenarios (Happy Path)
| Test ID | Scenario Description | Expected Result | Pass/Fail |
| :--- | :--- | :--- | :--- |
| **TC-01** | Student submits a 2-day Personal Leave. | Form submits successfully; routed to Faculty queue; status is 'Pending Faculty'. | |
| **TC-02** | Student submits a 5-day Medical Leave with a PDF. | Form submits successfully; routed to Faculty queue; attachment is saved. | |
| **TC-03** | Faculty Approves the 2-day Personal Leave (TC-01). | Status changes to 'Approved'; email sent to Student. | |
| **TC-04** | Faculty Approves the 5-day Medical Leave (TC-02). | Status changes to 'Pending HOD'; email sent to HOD. | |

### 1.2 Negative Scenarios (Error Handling)
| Test ID | Scenario Description | Expected Result | Pass/Fail |
| :--- | :--- | :--- | :--- |
| **TC-05** | Student attempts to submit Medical Leave WITHOUT an attachment. | System blocks submission; shows inline error: "Attachment required for Medical Leave." | |
| **TC-06** | Student uploads an executable (.exe) file instead of PDF. | System rejects file type; shows error: "Invalid file format." | |
| **TC-07** | Faculty attempts to 'Reject' a leave without adding comments. | System disables the submit button; prompts for mandatory comment. | |

### 1.3 Boundary Scenarios
| Test ID | Scenario Description | Expected Result | Pass/Fail |
| :--- | :--- | :--- | :--- |
| **TC-08** | Student selects an End Date that is before the Start Date. | Calendar logic prevents selection, or validation throws an error. | |
| **TC-09** | Student attempts to apply for a leave 4 days in the past (Rule: Max 3 days retroactive). | Date picker disables dates older than 3 days. | |
| **TC-10** | Student uploads an exact 5.0 MB PDF file. | System accepts the upload. | |
| **TC-11** | Student uploads a 5.1 MB PDF file. | System rejects upload; shows size limit error. | |

## 2. User Acceptance Testing (UAT)

**Target Audience for UAT:** 5 Students, 2 Faculty Members, 1 HOD, 1 Admin.

**UAT Script Example (For Faculty):**
1. Log into the staging URL using your provided test credentials.
2. Navigate to the 'Pending Approvals' dashboard.
3. Locate the request from "Test Student A".
4. Review the details and click 'Approve'.
5. **Sign-off Criteria:** Did the request disappear from your queue? Did you find the interface intuitive? (Yes/No - Comments).
