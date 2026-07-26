# Dashboard & KPIs

## 1. Overview
The Admin and HOD dashboards are critical for monitoring system health and identifying attendance trends. This document defines the Key Performance Indicators (KPIs) to be displayed on these dashboards.

## 2. Core KPIs

| KPI Name | Description | Target / Threshold | Visualization Type | Data Source |
| :--- | :--- | :--- | :--- | :--- |
| **Pending Requests** | Total number of leave requests currently awaiting approval across the department. | < 10 at any given time | Large Number Widget (Red if >10) | `SELECT count(*) FROM LeaveRequest WHERE status = 'Pending'` |
| **Approved Leaves** | Total leaves approved in the current month. | N/A (Informational) | Large Number Widget (Green) | `SELECT count(*) FROM LeaveRequest WHERE status = 'Approved'` |
| **Rejected Leaves** | Total leaves rejected in the current month. | N/A (Informational) | Large Number Widget (Orange) | `SELECT count(*) FROM LeaveRequest WHERE status = 'Rejected'` |
| **Average Approval Time (TAT)** | The average time taken from request submission to final decision. | < 24 Hours | Gauge Chart | Timestamp Diff (Submit vs Final Action) |

## 3. Graphical Dashboards

### 3.1 Department-wise Statistics
**Purpose:** To allow Management and Admin to see which departments have the highest absenteeism rates.
- **Chart Type:** Vertical Bar Chart
- **X-Axis:** Departments (e.g., Computer Science, Mechanical, Civil)
- **Y-Axis:** Total days of approved leave (Current Month)
- **Insight:** Helps allocate resources or identify systemic issues within a specific department.

### 3.2 Monthly Trends
**Purpose:** To track whether absenteeism is increasing or decreasing over the academic year.
- **Chart Type:** Line Chart
- **X-Axis:** Months (Jan, Feb, Mar, etc.)
- **Y-Axis:** Total leave applications submitted.
- **Insight:** Predict peak leave periods (e.g., right before exams or holidays) to adjust faculty staffing.

### 3.3 Leave Types Distribution
**Purpose:** To understand why students are taking leave.
- **Chart Type:** Pie Chart
- **Slices:** Medical (40%), Personal (30%), Event/Sports (20%), Other (10%)
- **Insight:** If 'Medical' spikes unexpectedly, it could indicate a campus health issue requiring intervention.

## 4. Dashboard Mockup Representation
```text
[ ADMIN DASHBOARD ]

+----------------+    +----------------+    +----------------+    +----------------+
| PENDING: 8     |    | APPROVED: 145  |    | REJECTED: 12   |    | AVG TAT: 18hrs |
+----------------+    +----------------+    +----------------+    +----------------+

[ Leave Types (Pie Chart) ]       [ Monthly Trend (Line Chart) ]
   ( ) Medical: 45%                    ^
   ( ) Personal: 35%                   |   /--\
   ( ) Event: 20%                      |  /    \__
                                       +-----------> (Time)

[ Department-wise Statistics (Bar Chart) ]

|   _
|  | |   _
|  | |  | |   _
|__|_|__|_|__|_|____
  CS   MECH  CIVIL
```
