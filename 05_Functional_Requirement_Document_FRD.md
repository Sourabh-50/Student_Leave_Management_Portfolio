# Functional Requirement Document (FRD)

## 1. Introduction
This document details the functional behavior, validation rules, and system responses for the Student Leave Management System (SLMS). It serves as a guide for the development and QA teams.

## 2. Functional Requirements

### 2.1 User Authentication & Authorization
| Req ID | Requirement Description | Priority | Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **FR-01** | The system shall allow users to log in using their existing institutional credentials (SSO). | High | User is authenticated against the Active Directory and routed to the correct role-based dashboard. |
| **FR-02** | The system shall enforce role-based access control (RBAC) for Student, Faculty, HOD, and Admin. | High | A student cannot access the HOD dashboard; UI elements are hidden based on role. |

### 2.2 Leave Application (Student Module)
| Req ID | Requirement Description | Priority | Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **FR-03** | The system shall provide a form with fields: Leave Type, Start Date, End Date, Reason, and Attachment. | High | Form renders correctly; mandatory fields are enforced. |
| **FR-04** | The system shall auto-calculate the total number of leave days based on Start and End dates. | High | Excludes weekends and institutional holidays in the calculation. |
| **FR-05** | The system shall allow file uploads (PDF, JPG, PNG) up to 5MB for medical certificates. | High | System accepts valid formats, rejects invalid ones, and enforces the 5MB size limit. |
| **FR-06** | The system shall allow students to cancel a pending leave request. | Medium | Request status changes to 'Cancelled'; workflow is halted. |

### 2.3 Leave Approval (Faculty / HOD Module)
| Req ID | Requirement Description | Priority | Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **FR-07** | The system shall display a dashboard of 'Pending Requests' to approvers. | High | Approvers see a sortable, filterable list of requests awaiting their action. |
| **FR-08** | The system shall allow approvers to 'Approve', 'Reject', or 'Request Info'. | High | Clicking a button updates the status and prompts for mandatory comments on Rejection. |
| **FR-09** | The system shall display the student's leave history (Total leaves taken this semester) on the approval screen. | High | Approver can view a summary card showing past approved leaves. |

### 2.4 Notifications
| Req ID | Requirement Description | Priority | Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **FR-10** | The system shall send an email notification to the Faculty when a new request is submitted. | High | Email triggers immediately upon form submission containing student name and dates. |
| **FR-11** | The system shall send an email to the student when the request status changes (Approved/Rejected). | High | Student receives timely update with any approver comments included. |

### 2.5 Reports & Dashboards (Admin/HOD Module)
| Req ID | Requirement Description | Priority | Acceptance Criteria |
| :--- | :--- | :--- | :--- |
| **FR-12** | The system shall generate a monthly departmental absenteeism report. | Medium | Report shows total leaves per student, exportable to CSV/Excel. |
| **FR-13** | The system shall display KPI widgets (Pending, Approved, Rejected) on the Admin dashboard. | Low | Widgets update in real-time based on database state. |

## 3. Business & Validation Rules
*   **VR-01 (Date Logic):** 'End Date' cannot be earlier than 'Start Date'. System must throw an inline error: *"End date must be after start date."*
*   **VR-02 (Past Dates):** 'Start Date' cannot be more than 3 days in the past. System must disable dates in the calendar picker accordingly.
*   **VR-03 (Mandatory Attachment):** If 'Leave Type' == 'Medical', the Attachment field becomes mandatory. Form submission is blocked if empty.

## 4. System Behavior & Error Handling
*   **Data Validation Errors:** Inline red text under the specific field; submit button disabled until resolved.
*   **Timeout:** If the user is inactive for 30 minutes, the system shall auto-logout and redirect to the login screen with the message *"Session expired due to inactivity."*
*   **System Failure:** In case of database connection failure during submission, display: *"An unexpected error occurred. Please try again later or contact IT."* Data should not be partially saved.
