# Low Fidelity Wireframes

*Note: As a Business Analyst, wireframes are used to communicate requirements to the UI/UX team. Below are ASCII representations of the core screens.*

## 1. Student Dashboard & Leave Application Screen
**Purpose:** Allows students to see their status and apply for new leave.

```text
+-----------------------------------------------------------------------------+
|  [Logo] SLMS Portal                  Welcome, Rahul Sharma (Student) [Logout] |
+-----------------------------------------------------------------------------+
|  +---------------------------+  +-----------------------------------------+ |
|  | MENU                      |  | MY LEAVE SUMMARY                        | |
|  | - Dashboard (Active)      |  | Total Leaves Taken: 4 Days              | |
|  | - Apply for Leave         |  | Current Attendance: 82%                 | |
|  | - History                 |  +-----------------------------------------+ |
|  | - Profile                 |  |                                         | |
|  +---------------------------+  | +-------------------------------------+ | |
|                                 | | RECENT REQUESTS              [New +]| | |
|                                 | |-------------------------------------| | |
|                                 | | Date   | Type    | Status           | | |
|                                 | | 12 Oct | Medical | [ Approved ]     | | |
|                                 | | 28 Oct | Personal| [ Pending ]      | | |
|                                 | +-------------------------------------+ | |
+-----------------------------------------------------------------------------+
```
**Explanation:** A clean layout showing critical metrics immediately. The "[New +]" button launches a modal for the application form.

## 2. Leave Application Modal (Form)
**Purpose:** The actual form fields required to satisfy BR-01 and FR-03.

```text
+-------------------------------------------------------------+
| Apply for Leave                                         [X] |
+-------------------------------------------------------------+
|                                                             |
| Leave Type: [ Dropdown: Medical, Personal, Event ]          |
|                                                             |
| Start Date: [ MM/DD/YYYY ] (Calendar Icon)                  |
| End Date:   [ MM/DD/YYYY ] (Calendar Icon)                  |
|                                                             |
| Total Days Calculated: 2                                    |
|                                                             |
| Reason:                                                     |
| [ Text Area ............................................]   |
| [ ......................................................]   |
|                                                             |
| Attachment (Mandatory for Medical):                         |
| [ Choose File ] No file chosen  (Max 5MB PDF/JPG)           |
|                                                             |
|                      [ Cancel ] [ Submit Request ]          |
+-------------------------------------------------------------+
```

## 3. Faculty Approval Dashboard
**Purpose:** A high-efficiency queue for approvers to quickly process requests.

```text
+-----------------------------------------------------------------------------+
|  [Logo] SLMS Portal                  Welcome, Prof. Desai (Faculty)  [Logout] |
+-----------------------------------------------------------------------------+
|                                                                             |
|  PENDING APPROVALS (3)                                                      |
|  +-----------------------------------------------------------------------+  |
|  | Student Name | Roll No | Dates         | Days | Type    | Action      |  |
|  |--------------|---------|---------------|------|---------|-------------|  |
|  | Amit Singh   | CS-012  | 01 Nov-02 Nov |  2   | Medical | [Review]    |  |
|  | Neha Gupta   | CS-045  | 05 Nov-08 Nov |  4   | Personal| [Review]    |  |
|  | Raj Patel    | CS-088  | 02 Nov-02 Nov |  1   | Event   | [Review]    |  |
|  +-----------------------------------------------------------------------+  |
|                                                                             |
+-----------------------------------------------------------------------------+
```

## 4. Faculty Review Modal
**Purpose:** Shows all information needed for the Faculty to make an informed decision (US-11, US-12).

```text
+-------------------------------------------------------------+
| Review Leave Request - Amit Singh                       [X] |
+-------------------------------------------------------------+
|                                                             |
| Student: Amit Singh (CS-012)                                |
| Current Attendance: 74% (Warning)                           |
| Leaves Taken this Semester: 6 Days                          |
|                                                             |
| Request Details:                                            |
| Dates: 01 Nov to 02 Nov (2 Days)                            |
| Type: Medical                                               |
| Reason: "Suffering from high fever, attached doctor note."  |
| Attachment: [ doctor_note.pdf ] (Click to view)             |
|                                                             |
| ----------------------------------------------------------- |
| Approver Comments (Required if rejecting):                  |
| [ ......................................................]   |
|                                                             |
|                      [ REJECT ] [ APPROVE ]                 |
+-------------------------------------------------------------+
```
