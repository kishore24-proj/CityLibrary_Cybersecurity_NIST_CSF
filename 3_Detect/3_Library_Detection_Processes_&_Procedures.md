# Detection Processes & Procedures Library

## 1. Purpose & Scope

This document catalogs all repeatable detection processes and associated procedures for the Detect function. It standardizes workflows from alert triage through rule tuning, ensuring consistency, auditability, and continuous improvement.

---

## 2. Process Catalog

| Process ID | Name                           | Description                                            | Owner                  | Frequency          | Input                              | Output                              | Tools                       |
|------------|--------------------------------|--------------------------------------------------------|------------------------|--------------------|------------------------------------|-------------------------------------|-----------------------------|
| P-001      | Alert Triage                   | Initial review, validation, and categorization of alerts | SOC Tier-1 Lead        | Continuous         | SIEM alerts stream                 | Validated tickets, false-positive feedback | SIEM, Ticketing System     |
| P-002      | Rule Development & Onboarding  | Design, test, and deploy new detection rules           | Detection Engineer     | As needed          | Use case spec, event mappings      | Deployed detection rule              | Git, Test Framework, CI/CD |
| P-003      | Alert Enrichment               | Augment alerts with threat intel and asset context      | Enrichment Analyst     | Continuous         | Validated alerts                   | Enriched alert records               | TIP, CMDB                   |
| P-004      | Incident Escalation            | Promote confirmed alerts to incident response           | SOC Tier-2 Lead        | As needed          | Enriched alerts                    | Incident tickets, escalation notes   | IR Platform                 |
| P-005      | Rule Tuning & Review           | Periodic review and adjustment of detection thresholds  | Detection Manager      | Monthly            | Metrics reports, false-positive logs | Tuned threshold settings             | SIEM, Reporting Dashboard   |
| P-006      | Log Source Onboarding          | Integrate new log/data sources into detection pipeline  | Log Engineer           | Project-based      | Source spec, network access        | Normalized log ingestion             | Log Collector, Parser       |
| P-007      | Feedback & Continuous Improvement | Collect and act on operational feedback                | Detection Program Lead | Quarterly          | Tuning tickets, analyst input      | Process updates, new use cases       | Jira, Confluence            |

---

## 3. Process Details

### P-001: Alert Triage

Description  
The tier-1 SOC team validates incoming alerts for true threats, filters noise, and assigns severity and ownership.

Steps  
1. Pull new alerts from SIEM.  
2. Cross-check against known false-positive signatures.  
3. Apply enrichment (user, asset, intel).  
4. Assign severity and create/close ticket.  
5. Record false positives and escalate confirmed incidents.

Roles & Responsibilities  
- SOC Tier-1: validate alerts, apply enrichment, document outcomes  
- SOC Tier-2: review escalated tickets, perform deeper analysis  

Inputs  
- Raw SIEM alerts  
- False-positive whitelist  

Outputs  
- Validated tickets in IR platform  
- False-positive feedback entries  

Success Metrics  
- Mean Time to Triage (MTTT)  
- False Positive Rate (FPR)  

---

### P-002: Rule Development & Onboarding

Description  
Defines the steps to author, test, peer-review, and deploy detection rules.

Steps  
1. Gather use case requirements.  
2. Map to event sources and fields.  
3. Write rule logic in test environment.  
4. Execute unit and integration tests.  
5. Peer-review in pull request.  
6. Merge and deploy via CI/CD.

Roles & Responsibilities  
- Detection Engineer: author and test rules  
- Peer Reviewers: validate logic and performance  
- DevOps: maintain CI/CD pipeline  

Inputs  
- Use case spec  
- Event mapping table  

Outputs  
- Production-ready detection rule  
- Test results report  

Success Metrics  
- Rule Coverage Rate  
- Test Pass Percentage  

---

### P-003: Alert Enrichment

Description  
Augments validated alerts with additional context to support rapid investigation.

Steps  
1. Enrich IPs with reputation data.  
2. Append asset criticality and owner.  
3. Tag alerts by threat
