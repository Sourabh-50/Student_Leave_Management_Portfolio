# Product Backlog

This backlog outlines the hierarchical structure of the requirements for the SLMS, mapped to proposed Agile Sprints.

## Sprint 1: Foundation & Core Application (Story Points: 35)
**Goal:** Setup basic architecture, authentication, and allow students to submit a basic leave request.

| Type | ID | Summary | Priority | Est. Points |
| :--- | :--- | :--- | :--- | :--- |
| Epic | EP-01 | **User Authentication & Profile** | High | - |
| Story| US-01 | Student Login via SSO | High | 5 |
| Story| US-02 | Role-based Dashboard Routing | High | 3 |
| Story| US-03 | View Student Profile | Medium | 3 |
| Epic | EP-02 | **Leave Application Management** | High | - |
| Story| US-04 | Calendar Date Selection Logic | High | 5 |
| Story| US-05 | Select Leave Type Dropdown | High | 2 |
| Story| US-06 | Upload Document Attachment | High | 8 |
| Story| US-07 | Text Reason input | Medium | 2 |
| Story| US-08 | Form Validation & Submit | High | 3 |
| Task | TK-01 | Set up React.js project repository | High | 2 |
| Task | TK-02 | Configure PostgreSQL database schema | High | 2 |

## Sprint 2: Workflow & Approvals (Story Points: 40)
**Goal:** Implement the approval dashboards for Faculty and HOD, and build the routing logic engine.

| Type | ID | Summary | Priority | Est. Points |
| :--- | :--- | :--- | :--- | :--- |
| Epic | EP-03 | **Leave Approval Workflow** | High | - |
| Story| US-10 | Faculty Pending Requests Data Grid | High | 5 |
| Story| US-11 | Request Detail Modal View | High | 5 |
| Story| US-13 | Faculty 'Approve' Action | High | 3 |
| Story| US-14 | Faculty 'Reject' Action with mandatory comments| High | 5 |
| Story| US-15 | System Routing Logic (>3 days to HOD) | High | 8 |
| Story| US-16 | HOD Pending Requests Queue | High | 3 |
| Story| US-17 | HOD Approve/Reject Actions | High | 3 |
| Story| US-09 | Student Cancel Request | Low | 3 |
| Task | TK-03 | Setup AWS S3 bucket for attachments | High | 5 |

## Sprint 3: Notifications, Admin & Analytics (Story Points: 35)
**Goal:** Close the communication loop with emails, build the admin master view, and implement basic reporting.

| Type | ID | Summary | Priority | Est. Points |
| :--- | :--- | :--- | :--- | :--- |
| Epic | EP-04 | **Notifications & Tracking** | Medium | - |
| Story| US-18 | Student Status Tracking Dashboard | High | 5 |
| Story| US-19 | Email Notification to Faculty (New Request) | Medium | 3 |
| Story| US-20 | Email Notification to Student (Final Decision)| High | 3 |
| Epic | EP-05 | **Admin & Reporting** | Medium | - |
| Story| US-21 | Admin Master Data Grid | High | 5 |
| Story| US-22 | Admin Search functionality | High | 3 |
| Story| US-12 | Display Student Leave History to Faculty | Medium | 5 |
| Story| US-23 | HOD Dashboard Pie Charts (Leave Types) | Low | 5 |
| Story| US-24 | Admin CSV Export functionality | Medium | 5 |
| Subtk| ST-01 | Integrate SendGrid API for SMTP | Medium | 1 |
