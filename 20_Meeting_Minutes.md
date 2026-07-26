# Meeting Minutes (MOM)

## 1. Requirement Gathering Kickoff
**Date:** Oct 2, 2023  
**Time:** 10:00 AM - 11:30 AM  
**Attendees:** Principal, HOD (CS), Head of Admin, BA (Me), IT Lead.  

**Agenda:** 
- Identify pain points in the current paper-based leave process.
- Define high-level project objectives for the SLMS.

**Discussion Points:**
- **Admin Head:** Highlighted that physical storage of medical certificates is becoming impossible. Requested digital uploads.
- **HOD:** Insisted that he only wants to see leaves longer than 3 days. Anything less should be handled by Faculty.
- **IT Lead:** Confirmed that the Active Directory (AD) can be used for Single Sign-On (SSO).

**Action Items:**
- **BA:** Draft the initial BRD incorporating the >3-day routing rule. (Due: Oct 10)
- **IT Lead:** Check API documentation for the legacy SIS. (Due: Oct 5)

---

## 2. Sprint 1 Planning Meeting
**Date:** Oct 25, 2023  
**Time:** 9:00 AM - 10:00 AM  
**Attendees:** Scrum Master, BA (Me), Dev Team (3), QA (1).  

**Agenda:** 
- Review prioritized backlog for Sprint 1.
- Estimate User Stories using Planning Poker.

**Discussion Points:**
- BA presented Epic 1 (Authentication) and Epic 2 (Leave Application).
- Dev Team raised a technical question regarding the file storage for attachments (US-06). Decided to use AWS S3. Story points increased from 5 to 8 to account for S3 configuration.
- Total Sprint capacity agreed upon: 35 Story Points.

**Action Items:**
- **Dev Team:** Begin environment setup and Jira task creation.
- **BA:** Ensure wireframes are attached to all Sprint 1 Jira tickets by EOD.

---

## 3. Client Review / Demo (Sprint 2)
**Date:** Nov 15, 2023  
**Time:** 2:00 PM - 3:00 PM  
**Attendees:** HOD (CS), Head of Admin, BA (Me), Dev Lead.  

**Agenda:** 
- Demo the Faculty and HOD approval workflows developed in Sprint 2.

**Discussion Points:**
- Dev Lead walked through the UI. Submitted a 4-day leave and showed it appearing in the HOD's queue.
- **HOD Feedback:** "The UI looks great, but I need to see the student's *current attendance percentage* on the approval screen, not just the number of leaves taken."
- BA acknowledged this as a valid change request (CR).

**Action Items:**
- **BA:** Write a new User Story for adding the Attendance % to the modal and add it to Sprint 3.

---

## 4. Project Closure & Go-Live Sign-off
**Date:** Dec 5, 2023  
**Time:** 11:00 AM - 11:30 AM  
**Attendees:** Principal, Project Sponsor, IT Lead, BA (Me).  

**Agenda:** 
- Review UAT results.
- Formal sign-off for Production Go-Live.

**Discussion Points:**
- BA presented the UAT report: 100% pass rate on critical functional scenarios.
- IT Lead confirmed servers are provisioned and load tested.
- Principal formally approved the rollout to the student body for the Spring semester.

**Action Items:**
- **Admin:** Send out a mass email to students with the new portal link and a "How-To" PDF.
