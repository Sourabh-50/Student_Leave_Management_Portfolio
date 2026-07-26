# Agile Artifacts & Ceremonies

This document outlines how Agile Scrum was implemented during the SLMS project lifecycle.

## 1. Definition of Ready (DoR)
Before a User Story from the backlog can be pulled into a Sprint, it must meet the following criteria:
*   The story is written in the standard "As a... I want to... So that..." format.
*   Clear Acceptance Criteria are defined.
*   Wireframes/Mockups are attached (if it is a UI task).
*   Dependencies are identified and resolved.
*   The story has been estimated by the Dev Team (Story Points).

## 2. Definition of Done (DoD)
A User Story is not considered "Done" until:
*   Code is complete and peer-reviewed.
*   Unit tests are written and passing.
*   The feature passes QA testing in the staging environment.
*   No high-priority bugs exist for the feature.
*   Product Owner (or BA acting as proxy) has accepted the feature.

## 3. Daily Standup Summary (Example)
**Date:** Oct 28 (Sprint 1, Day 3)
*   **Dev 1 (Frontend):** 
    *   *Yesterday:* Built the Student login UI.
    *   *Today:* Integrating SSO AD token.
    *   *Blockers:* None.
*   **Dev 2 (Backend):** 
    *   *Yesterday:* Configured PostgreSQL schema.
    *   *Today:* Writing APIs for form submission.
    *   *Blockers:* Waiting for S3 bucket credentials from IT.
*   **BA (Me):** Followed up with IT to get the S3 credentials for Dev 2. Unblocked the team.

## 4. Sprint Review (Demo)
*   **Sprint 1 Review Outcome:** The team successfully demonstrated the student application form to the stakeholders. The Principal was pleased with the mobile responsiveness.
*   **Feedback:** The HOD requested that the 'Reason' text box be expanded from 200 characters to 500 characters. BA added a small task to Sprint 2 backlog to address this.

## 5. Sprint Retrospective
**Sprint 1 Retrospective Notes:**
*   **What went well:** The team hit their velocity target of 35 points. UI components were built faster than expected.
*   **What could be improved:** Requirements around the SIS integration were initially vague, causing backend delays.
*   **Action Item for Next Sprint:** BA to schedule a dedicated 30-minute technical session with the IT Lead before Sprint 2 planning to finalize all API contracts.
