# Risk Register

This document outlines potential risks identified during the planning phase of the SLMS, along with their assessments and mitigation strategies.

| Risk ID | Risk Description | Category | Probability (1-5) | Impact (1-5) | Score (P*I) | Mitigation Strategy | Owner | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **R-01** | **Low User Adoption by Faculty**<br>Faculty may resist transitioning from paper to a digital system. | Operational | 3 | 4 | 12 (High) | Conduct comprehensive hands-on training sessions and mandate the transition via a directive from the Principal. | Change Management Team | Active |
| **R-02** | **SIS Integration Failure**<br>The API to fetch student data from the legacy SIS might be unstable. | Technical | 2 | 5 | 10 (High) | Develop a fallback mechanism (nightly CSV batch upload) to ensure SLMS can function independently if the API goes down. | IT / Dev Lead | Active |
| **R-03** | **Data Privacy Breach**<br>Medical certificates uploaded by students contain sensitive PII/PHI that could be leaked. | Security | 1 | 5 | 5 (Med) | Enforce AES-256 encryption on the S3 bucket; restrict document viewing access strictly to the assigned Approver and Admin. | SecOps Team | Mitigated |
| **R-04** | **Scope Creep**<br>HODs may request payroll/faculty leave features to be added to this student-only system. | Project Management | 4 | 3 | 12 (High) | Maintain strict adherence to the signed BRD. Push any non-student features to Phase 2 (Backlog). | Business Analyst | Active |
| **R-05** | **Server Overload**<br>High concurrent usage during exam weeks may crash the server. | Technical | 2 | 4 | 8 (Med) | Implement auto-scaling cloud infrastructure and conduct stress/load testing prior to UAT. | DevOps Engineer | Active |
