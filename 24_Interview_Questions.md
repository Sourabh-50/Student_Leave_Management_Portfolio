# Business Analyst Interview Questions (Based on SLMS Project)

## Requirement Elicitation & Planning
1.  **Q:** How did you gather requirements for the SLMS project?
    *   **A:** I conducted stakeholder interviews with the Principal, HODs, and Admin staff. I also shadowed the Admin clerk to observe the AS-IS manual paper process.
2.  **Q:** Who were the key stakeholders, and how did you manage conflicting requirements?
    *   **A:** Stakeholders included Students, Faculty, HODs, and Admin. When the HOD requested a feature that conflicted with IT security constraints (viewing all student medical data), I facilitated a compromise where only the direct Approver could view the attachment.
3.  **Q:** How did you identify the root cause of the delays in the old system?
    *   **A:** I used the '5 Whys' technique, which revealed that the lack of centralized digital ownership was the core issue, not just "slow faculty."
4.  **Q:** What was the most challenging requirement to define?
    *   **A:** The dynamic routing logic (>3 days vs <=3 days) required precise business rules to ensure edge cases (e.g., weekends) were handled correctly.
5.  **Q:** How did you ensure you didn't miss any requirements?
    *   **A:** I created a comprehensive Requirement Traceability Matrix (RTM) linking business objectives to user stories and test cases.

## Documentation & Diagrams
6.  **Q:** What is the difference between the BRD and the FRD you created for this project?
    *   **A:** The BRD focused on the "Why" and "What" (business goals, high-level scope), while the FRD focused on the "How" (system behavior, validations, UI interactions).
7.  **Q:** Walk me through the BPMN diagram you created for the AS-IS process.
    *   **A:** It showed the manual hand-offs. A student requests a paper form, fills it, physically hands it to faculty, and eventually it reaches admin for manual data entry.
8.  **Q:** Why did you use a Sequence Diagram?
    *   **A:** I used it to illustrate the backend logic of the approval workflow, showing how the UI interacts with the API, Database, and SMTP email service.
9.  **Q:** Explain a specific business rule you documented.
    *   **A:** "If Leave Type = Medical, then Attachment Upload = Mandatory." I documented this in the FRD to ensure developers built proper form validation.
10. **Q:** Did you create wireframes? What tools did you use?
    *   **A:** Yes, I created low-fidelity wireframes using [Balsamiq/Figma/Draw.io] to visually communicate the Dashboard layout to the developers.

## Agile & Scrum
11. **Q:** How did you structure the Product Backlog?
    *   **A:** I broke the project into Epics (e.g., Authentication, Leave Application), then Features, and finally detailed User Stories.
12. **Q:** Give me an example of a User Story you wrote for the SLMS.
    *   **A:** "As a Student, I want to view my leave history, so that I know my current attendance percentage."
13. **Q:** What Acceptance Criteria did you write for the Medical Leave story?
    *   **A:** 1. Supports PDF/JPG. 2. Max size 5MB. 3. System blocks submission if empty.
14. **Q:** How were story points assigned in your team?
    *   **A:** We used Planning Poker during Sprint Planning to reach a consensus based on complexity and effort.
15. **Q:** What was your role during the Daily Standup?
    *   **A:** As a BA, I listened for any requirements-related blockers and clarified doubts the developers had regarding the acceptance criteria.
16. **Q:** How did you handle scope creep during a sprint?
    *   **A:** When the HOD asked for a new dashboard chart mid-sprint, I documented it as a new User Story and placed it in the backlog for prioritization in the next sprint, protecting the current sprint goal.
17. **Q:** What is your Definition of Ready (DoR)?
    *   **A:** A story is Ready when it has clear Acceptance Criteria, necessary wireframes, and has been estimated by the dev team.
18. **Q:** What is your Definition of Done (DoD)?
    *   **A:** Code is written, tested, passes UAT, and is signed off by the product owner.
19. **Q:** How did you use the Sprint Retrospective?
    *   **A:** We reviewed our velocity. In one retro, we realized API dependencies were blocking us, so we agreed to finalize API contracts earlier in the next sprint.
20. **Q:** Were you a Product Owner or a BA?
    *   **A:** I acted as a BA, serving as a proxy Product Owner by managing the backlog and prioritizing stories based on stakeholder value.

## Functional & Technical Analysis
21. **Q:** What non-functional requirements (NFRs) did you define in the SRS?
    *   **A:** I defined security (AES-256 encryption for medical docs), performance (<2s response time), and availability (99.9% uptime).
22. **Q:** How did the SLMS handle weekends in the leave calculation?
    *   **A:** I defined a business rule that the system's date calculator must exclude weekends and institutional holidays from the "Total Days" count.
23. **Q:** How did you handle user roles and permissions?
    *   **A:** Defined an RBAC (Role-Based Access Control) matrix. Students only see their data; Faculty see their class; HODs see the department.
24. **Q:** What happens if a Faculty member rejects a leave?
    *   **A:** The system enforces a mandatory comment field, updates the status to 'Rejected', and triggers an email to the student with the reason.
25. **Q:** How did you integrate the legacy SIS?
    *   **A:** We used a REST API for a one-way daily sync of student data (Name, Roll No) into our PostgreSQL database.
26. **Q:** What happens if the SIS API goes down?
    *   **A:** I identified this in the Risk Register and proposed a fallback mechanism—a daily CSV batch upload.
27. **Q:** Explain the data schema for the Leave Request object.
    *   **A:** It contains Student ID, Start Date, End Date, Type, Reason, Status, and Attachment URL.
28. **Q:** How did you design the notification system?
    *   **A:** Trigger-based logic. Status change in the DB triggers an SMTP API call to SendGrid to fire an email template.
29. **Q:** How did you handle historical data from the old paper system?
    *   **A:** We defined it as Out of Scope for Phase 1. The SLMS started with a clean slate for the new semester to avoid massive manual data entry.
30. **Q:** What KPIs did you include on the Admin Dashboard?
    *   **A:** Pending Requests, Average Turnaround Time (TAT), and Department-wise absenteeism (bar chart).

## Testing & Quality Assurance
31. **Q:** What was your role during testing?
    *   **A:** I wrote the UAT test scenarios and facilitated the UAT sessions with the end-users (Faculty and Admin).
32. **Q:** Give an example of a negative test case you wrote.
    *   **A:** "Attempt to submit a leave request where the End Date is before the Start Date."
33. **Q:** Give an example of a boundary test case.
    *   **A:** "Upload an attachment that is exactly 5.1MB to verify the size limit validation."
34. **Q:** What was a bug found during UAT, and how was it handled?
    *   **A:** An approver noticed holidays were being counted as leave days. I logged it as a high-priority defect, and the dev team fixed the date calculation logic before Go-Live.
35. **Q:** How did you ensure all requirements were tested?
    *   **A:** By using the RTM to map every FRD item to a specific Test Case ID.

## Impact & Leadership
36. **Q:** What was the ROI of this project?
    *   **A:** We reduced approval TAT by 80%, saved the admin team 15 hours/week in data entry, and eliminated paper costs.
37. **Q:** How did you handle resistance to change from older faculty members?
    *   **A:** I conducted hands-on training sessions and highlighted the "WIIFM" (What's in it for me) factor—showing them how much time they would save not dealing with paper.
38. **Q:** Tell me about a time you had to push back on a stakeholder.
    *   **A:** The HOD wanted to add faculty payroll tracking to the system. I pushed back, explaining it violated the project scope, and documented it for a future phase.
39. **Q:** What was your biggest learning from this project?
    *   **A:** The importance of defining edge cases early. For example, realizing mid-sprint that we hadn't defined what happens if a student tries to apply for leave retroactively.
40. **Q:** If you could do this project again, what would you change?
    *   **A:** I would have involved the UI/UX designer earlier in the requirement phase to create high-fidelity prototypes, which would have made stakeholder sign-off even faster.

*(Note: Questions 41-50 can follow similar situational formats, focusing on specific Agile ceremonies, data mapping, API concepts, and stakeholder communication).*
