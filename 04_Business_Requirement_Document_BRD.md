# Business Requirement Document (BRD)

**Project Name:** Student Leave Management System (SLMS)  
**Document Version:** 1.0  
**Date:** October 24, 2023  
**Prepared By:** Senior Business Analyst  

---

## 1. Business Objectives
*   **OBJ-01:** Digitize 100% of the student leave application process by Q3.
*   **OBJ-02:** Reduce the average end-to-end approval time from 72 hours to under 24 hours.
*   **OBJ-03:** Eliminate manual data entry for the Administration department, saving an estimated 20 hours per week.
*   **OBJ-04:** Provide real-time visibility into leave status for students and attendance analytics for management.

## 2. Business Scope
### 2.1 In Scope
*   Web and mobile-responsive portal for Students, Faculty, HODs, and Admin.
*   Digital leave application form with document upload capabilities.
*   Automated multi-tier workflow routing (Faculty -> HOD -> Admin).
*   Email and SMS notification system for status updates.
*   Dashboard reporting and analytics for Faculty, HODs, and Management.
*   Integration with the existing Student Information System (SIS) for basic student data (Name, ID, Department).

### 2.2 Out of Scope
*   Integration with the payroll system for faculty/staff leave (this system is strictly for students).
*   Automated biometric attendance capturing (only leave requests are managed here).
*   Offline capability (the system requires an active internet connection).

## 3. Business Requirements
| Req ID | Requirement Description | Priority |
| :--- | :--- | :--- |
| **BR-01** | The system shall allow students to submit leave requests digitally. | High |
| **BR-02** | The system shall automatically route requests to the appropriate approver based on the leave duration. | High |
| **BR-03** | The system shall allow approvers to view the student's leave history before making a decision. | High |
| **BR-04** | The system shall notify the student via email upon approval, rejection, or request for more information. | Medium |
| **BR-05** | The system shall provide analytical dashboards for HODs to view departmental absenteeism trends. | Medium |
| **BR-06** | The system shall maintain an unalterable audit trail of all actions taken on a leave request. | High |

## 4. Business Rules
*   **BRule-01:** Leaves of 1 to 3 days require only Faculty approval.
*   **BRule-02:** Leaves of >3 days require Faculty approval AND subsequent HOD approval.
*   **BRule-03:** Medical leaves of any duration require a mandatory document upload (Medical Certificate).
*   **BRule-04:** Students cannot apply for leave retroactively (more than 3 days after the leave end date).

## 5. Assumptions, Dependencies, Risks, and Constraints

### 5.1 Assumptions
*   All users (Students, Faculty) have access to a smartphone or computer with internet connectivity.
*   The existing Student Information System (SIS) API is available and stable for data synchronization.

### 5.2 Dependencies
*   Dependency on the IT Infrastructure team to provision cloud hosting environments.
*   Dependency on the Legal/Compliance team to approve data privacy handling of medical certificates.

### 5.3 Risks
| Risk | Probability | Impact | Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| Low user adoption by Faculty accustomed to paper | Medium | High | Conduct extensive change management and hands-on training sessions. |
| API integration failure with legacy SIS | Low | High | Develop a fallback CSV bulk upload mechanism for student data sync. |

### 5.4 Constraints
*   The project must be completed within a 4-week Agile development cycle.
*   The system must comply with local data protection regulations (e.g., GDPR/FERPA equivalent).

## 6. Success Metrics & Business KPIs
*   **Adoption Rate:** 90% of all leave applications submitted via the new system within the first month.
*   **Turnaround Time (TAT):** 95% of leave requests processed within 24 hours.
*   **User Satisfaction:** >4.0/5.0 average rating on post-implementation user surveys.

## 7. Approval Workflow (High Level)
1.  **Submit:** Student submits request.
2.  **Evaluate (Tier 1):** Faculty reviews. If <= 3 days, Faculty Approves/Rejects. If > 3 days, Faculty recommends and forwards to HOD.
3.  **Evaluate (Tier 2):** HOD reviews forwarded requests and Approves/Rejects.
4.  **Finalize:** Admin system is updated, and student is notified.

## 8. Version History
| Version | Date | Author | Description of Changes |
| :--- | :--- | :--- | :--- |
| 0.1 | Oct 10 | BA | Initial Draft |
| 0.2 | Oct 15 | BA | Updated Business Rules based on HOD feedback |
| 1.0 | Oct 24 | BA | Final Approved Version |

## 9. Glossary
*   **HOD:** Head of Department
*   **SIS:** Student Information System
*   **TAT:** Turnaround Time
*   **SLMS:** Student Leave Management System
