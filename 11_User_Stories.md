# User Stories

## Epic 1: User Authentication & Profile
| ID | As a... | I want to... | So that I can... | Acceptance Criteria | Priority | Story Points |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-01 | Student | Log in using my university email | Access the leave portal securely | 1. SSO integration works.<br>2. Error message on invalid credentials. | High | 5 |
| US-02 | Faculty | Be routed to the Faculty Dashboard upon login | See my specific approval queue | 1. System reads AD role.<br>2. Redirects to `/faculty-dash`. | High | 3 |
| US-03 | Student | View my profile and current attendance % | Know if I am eligible to take leave | 1. Profile displays Name, Roll No, Dept.<br>2. Shows attendance %. | Medium | 3 |

## Epic 2: Leave Application Management
| ID | As a... | I want to... | So that I can... | Acceptance Criteria | Priority | Story Points |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-04 | Student | Select leave start and end dates from a calendar | Define the duration of my leave | 1. Calendar widget present.<br>2. Past dates (>3 days) disabled.<br>3. End date must be >= Start date. | High | 5 |
| US-05 | Student | Select a 'Leave Type' (e.g., Medical, Personal) | Categorize my request appropriately | 1. Dropdown with predefined types. | High | 2 |
| US-06 | Student | Upload a document attachment | Provide medical proof for my absence | 1. Supports PDF, JPG.<br>2. Max size 5MB.<br>3. Mandatory if type='Medical'. | High | 8 |
| US-07 | Student | Add a text reason for my leave | Give context to the approver | 1. Textbox max 500 chars. | Medium | 2 |
| US-08 | Student | Click 'Submit' to finalize my request | Send it for approval | 1. Form validates before submit.<br>2. Success message shown. | High | 3 |
| US-09 | Student | Cancel a pending request | Retract it if my plans change | 1. Cancel button visible only if status is 'Pending'.<br>2. Status updates to 'Cancelled'. | Low | 3 |

## Epic 3: Leave Approval Workflow
| ID | As a... | I want to... | So that I can... | Acceptance Criteria | Priority | Story Points |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-10 | Faculty | View a list of pending requests | See who needs my approval | 1. Data grid showing Student Name, Dates, Status. | High | 5 |
| US-11 | Faculty | Click on a request to view details | See the reason and attachments | 1. Opens a modal with full details.<br>2. Attachment can be viewed/downloaded. | High | 5 |
| US-12 | Faculty | See the student's leave history on the detail view | Make an informed decision | 1. Shows "Leaves taken this semester: X". | Medium | 5 |
| US-13 | Faculty | Click 'Approve' on a 1-day leave | Grant permission | 1. Status changes to 'Approved'.<br>2. Removed from pending queue. | High | 3 |
| US-14 | Faculty | Click 'Reject' and provide a reason | Deny permission with context | 1. 'Reject' opens a mandatory comment box. | High | 5 |
| US-15 | System | Automatically route >3 day leaves to HOD | Ensure policy compliance | 1. When Faculty approves >3 days, status becomes 'Pending HOD'. | High | 8 |
| US-16 | HOD | View a queue of forwarded requests | Review long-term absences | 1. Queue only shows requests >3 days approved by Faculty. | High | 3 |
| US-17 | HOD | Approve or Reject requests | Finalize the workflow | 1. Similar UI to Faculty approval.<br>2. Final status applied. | High | 3 |

## Epic 4: Notifications & Tracking
| ID | As a... | I want to... | So that I can... | Acceptance Criteria | Priority | Story Points |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-18 | Student | View a dashboard of my request statuses | Track if I am approved | 1. Shows 'Pending', 'Approved', 'Rejected' pills. | High | 5 |
| US-19 | System | Send an email to Faculty on new submission | Alert them to act | 1. Email contains student name and dates. | Medium | 3 |
| US-20 | System | Send an email to the Student on final decision | Inform them immediately | 1. Email contains final status and approver comments. | High | 3 |

## Epic 5: Admin & Reporting
| ID | As a... | I want to... | So that I can... | Acceptance Criteria | Priority | Story Points |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| US-21 | Admin | View all approved leaves system-wide | Ensure database sync | 1. Master data grid with all approved records. | High | 5 |
| US-22 | Admin | Search for a specific student's record | Resolve queries quickly | 1. Search bar by Name or Roll No. | High | 3 |
| US-23 | HOD | View a pie chart of 'Leave Types' | Understand why students are absent | 1. Chart renders accurately based on department data. | Low | 5 |
| US-24 | HOD | Export a monthly report to Excel | Keep records for audits | 1. Export button generates a .csv file. | Medium | 5 |
| US-25 | Admin | Configure institutional holidays in the calendar | Ensure holidays aren't counted as leave | 1. Admin UI to add holiday dates.<br>2. Leave calculation skips these dates. | Medium | 8 |
