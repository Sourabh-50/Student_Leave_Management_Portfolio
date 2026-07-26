# Software Requirement Specification (SRS)

## 1. Introduction

### 1.1 Purpose
The purpose of this document is to define the software requirements for the Student Leave Management System (SLMS). It provides a detailed description of the system's intended capabilities, interfaces, and performance characteristics following IEEE standards. This document is intended for the development team, QA analysts, and project stakeholders.

### 1.2 Scope
The SLMS is a web-based application designed to automate the student leave application, routing, and approval process. It replaces the legacy paper-based system. The system interfaces with the existing institutional Student Information System (SIS) for user data but operates as a standalone workflow engine.

## 2. Overall Description

### 2.1 Product Perspective
The SLMS is an independent system that relies on a one-way sync from the SIS. It operates in a cloud environment and is accessed via standard web browsers (Chrome, Firefox, Safari, Edge) on desktop and mobile devices.

### 2.2 User Characteristics
- **Students:** Digitally literate, prefer mobile access, expect rapid responses.
- **Faculty/HOD:** Moderate to high digital literacy, prefer desktop interface for reviewing applications, value efficiency and minimal clicks.
- **Admin:** High system usage, require robust reporting and data export capabilities.

### 2.3 Assumptions and Dependencies
- **Assumption:** Users will not share login credentials.
- **Dependency:** The institution's Active Directory (AD) must be available for Single Sign-On (SSO) authentication.

## 3. Specific Requirements

### 3.1 Functional Requirements
*(Note: Refer to the Functional Requirement Document (FRD) for detailed user stories and functional validation rules. Key capabilities are summarized below.)*
- **REQ-F-01:** System shall authenticate users via Institutional SSO.
- **REQ-F-02:** System shall provide role-specific dashboards.
- **REQ-F-03:** System shall calculate workflow routing based on the 'Leave Duration' integer.
- **REQ-F-04:** System shall support PDF/JPEG uploads up to 5MB.
- **REQ-F-05:** System shall generate systemic email notifications via SMTP.

### 3.2 Non-Functional Requirements (NFR)

#### 3.2.1 Performance
- **REQ-NF-01 (Response Time):** 95% of standard page loads must complete within 2.0 seconds under normal load.
- **REQ-NF-02 (Throughput):** The system must handle up to 500 concurrent users without degradation in performance (e.g., during peak exam periods).

#### 3.2.2 Availability
- **REQ-NF-03 (Uptime):** The system shall guarantee 99.9% uptime during the academic semester (excluding planned maintenance windows occurring between 12:00 AM and 4:00 AM on Sundays).

#### 3.2.3 Security
- **REQ-NF-04 (Encryption in Transit):** All data transmitted between the client and server must be encrypted using TLS 1.2 or higher (HTTPS).
- **REQ-NF-05 (Encryption at Rest):** Database records, especially medical attachments, must be encrypted at rest using AES-256.
- **REQ-NF-06 (Data Privacy):** Medical documents are only viewable by the designated Approver and Admin; peers or unauthorized faculty cannot access them.

#### 3.2.4 Scalability
- **REQ-NF-07 (Horizontal Scaling):** The application architecture must support horizontal scaling (e.g., containerized deployment via Kubernetes) to handle future increases in student population.

#### 3.2.5 Reliability
- **REQ-NF-08 (Data Backup):** The database must perform automated, differential backups daily and full backups weekly, retained for 7 years as per institutional compliance.

## 4. Constraints
- The system must be developed using open-source technologies (e.g., React.js, Node.js, PostgreSQL) to avoid vendor lock-in and licensing fees.
- The UI must comply with WCAG 2.1 AA accessibility standards.
