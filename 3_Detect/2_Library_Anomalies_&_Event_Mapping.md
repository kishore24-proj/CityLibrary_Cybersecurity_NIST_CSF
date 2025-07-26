# Anomalies & Event Mapping

## 1. Purpose & Scope

This document defines how we classify and map detected anomalies to underlying event sources. It ensures every anomaly use case is traceable to one or more log events, enabling clear rule authoring, tuning, and investigation workflows.

---

## 2. Anomaly Definitions & Event Mapping

| Anomaly ID | Name                              | Description                                                 | Event Source                    | Key Fields / Indicators               | Detection Rule ID | Severity |
|------------|-----------------------------------|-------------------------------------------------------------|---------------------------------|---------------------------------------|-------------------|----------|
| A-001      | Unusual Login Geography           | User logs in from a location not seen in baseline history   | Windows Security Event (4624), Cloud Auth Logs | user.name, src.ip, geo.location     | R-101             | High     |
| A-002      | Multiple Failed Logon Attempts    | Excessive failed logins over short interval                  | Windows Security Event (4625), SSHD Logs         | user.name, src.ip, failure.count    | R-102             | Medium   |
| A-003      | New Administrative Account Created| Creation of a user with privileged group membership         | Windows Security Event (4720 & 4732), LDAP Logs  | user.name, group.name               | R-103             | High     |
| A-004      | Suspicious Process Spawn          | High-risk executable launched by non-standard parent process | Sysmon Event (1), Endpoint Process Logs          | parent.process, process.name        | R-104             | Medium   |
| A-005      | Data Exfiltration Spike           | Outbound data volume significantly above baseline            | Firewall Logs, Proxy Logs                       | src.ip, dst.ip, bytes.sent          | R-105             | High     |
| A-006      | Abnormal Service Configuration    | Changes to critical service parameters outside maintenance window | Windows Config Changes (7045), Linux Auditd Logs | service.name, change.params         | R-106             | Medium   |

---

## 3. Implementation Considerations

- Data Normalization  
  Ensure all logs conform to common field naming (e.g., `user.name`, `src.ip`, `event.time`) before feeding detection rules.

- Enrichment  
  Augment raw events with threat intelligence (IP reputation, country) and asset context (owner, criticality).

- Threshold Tuning  
  Adapt anomaly thresholds (e.g., failure count, data volume) per environment baseline and business hours.

- Tagging & Classification  
  Assign consistent tags (`anomaly`, `high-risk`, `user-behavior`) to events for easy filtering and dashboarding.

---

## 4. Dashboards & Alerts

- Anomaly Overview Dashboard  
  - Count of each anomaly type by severity and status  
  - Time-series of anomaly occurrences vs. baseline  

- Investigation Workbench  
  - Drill-down by Anomaly ID → raw event timeline → related alerts  

- Weekly Tuning Report  
  - False-positive rate by anomaly  
  - Suggested threshold adjustments  

---

## 5. Review Cadence & Stakeholders

| Cadence  | Participants                         | Activities                                               |
|----------|--------------------------------------|----------------------------------------------------------|
| Weekly   | SOC Analysts, Detection Engineers    | Review new anomalies, false positives, urgent tuning     |
| Monthly  | Threat Intel, IR Lead                | Validate enrichment sources, update event mappings       |
| Quarterly| CISO, Security Architects            | Assess coverage gaps, roadmap new anomaly detection use cases |

---

## 6. Change Log

| Version | Date       | Author   | Description                                    |
|---------|------------|----------|------------------------------------------------|
| 1.0     | 2025-07-26 | Kishore  | Initial anomaly/event mapping definitions      |
| 1.1     | 2025-08-10 | Kishore  | Added Data Exfiltration Spike, tuning notes    |
| 1.2     | 2025-09-05 | Kishore  | Refined geolocation enrichment guidance        |
