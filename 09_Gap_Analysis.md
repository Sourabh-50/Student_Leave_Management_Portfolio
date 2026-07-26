# Gap Analysis

## 1. Overview
This document compares the Current State (AS-IS) of the student leave process with the desired Future State (TO-BE), identifying the operational and technological gaps that the SLMS project must bridge.

## 2. Gap Analysis Matrix

| Feature / Process | Current State (AS-IS) | Future State (TO-BE) | Identified Gap | Recommendation (Solution) | Priority | Benefit |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Application Method** | Physical paper forms retrieved from the admin office. | 100% digital web/mobile form. | Lack of a digital data entry portal. | Develop a responsive web portal for students. | High | Eliminates paper costs; allows 24/7 submission. |
| **Routing & Workflow** | Student physically carries the form to Faculty/HOD. | System automatically routes requests based on rules. | No automated workflow engine. | Implement a rule-based routing engine in the backend. | High | Reduces TAT from 3-5 days to <24 hours. |
| **Document Storage** | Medical certificates are stapled to forms and stored in filing cabinets. | Documents uploaded digitally (PDF/JPG) and stored in cloud. | No secure digital storage infrastructure. | Integrate AWS S3 or Azure Blob storage for attachments. | High | Prevents loss of documents; ensures compliance. |
| **Status Tracking** | Student has no visibility; must ask Faculty or Admin. | Real-time status tracker on Student dashboard. | Lack of transparency mechanisms. | Build a status tracking UI component (Pending -> Approved). | Medium | Improves student satisfaction and reduces admin queries. |
| **Notifications** | None. Purely verbal or manual check-ins. | Automated Email/SMS alerts at each stage. | No automated communication protocol. | Integrate SMTP email service (e.g., SendGrid) for alerts. | Medium | Keeps all stakeholders informed proactively. |
| **Reporting / Analytics** | Admin manually compiles monthly attendance on Excel. | Real-time dashboards for HOD/Management. | Data is siloed in physical ledgers; no BI tools. | Develop analytics dashboard using charts (Recharts/Chart.js). | Medium | Enables data-driven decisions on absenteeism. |
| **Authentication** | Physical signature verification. | Secure digital login (SSO). | No digital identity verification for this process. | Integrate with institutional Active Directory (OAuth/SAML). | High | Ensures security and non-repudiation of approvals. |

## 3. Summary of Recommendations
To successfully bridge the gaps, the project requires:
1. **Frontend Development:** Creation of role-based UI portals.
2. **Backend Logic:** Implementation of a business rules engine for routing.
3. **Database Architecture:** Transition from physical ledgers to a relational database (e.g., PostgreSQL).
4. **Integration:** Connecting with the existing AD for SSO and SMTP for communications.
