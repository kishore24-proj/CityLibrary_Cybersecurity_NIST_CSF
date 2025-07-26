# Detection Metrics & Reporting: Library

## 1. Purpose & Scope

This document defines how we measure and report on the effectiveness of our library’s Detect-phase controls. It covers key performance indicators for all detection rules, anomaly models, and monitoring processes in `3_Detect/`.

---

## 2. Metrics Definitions

| Metric ID | Name                             | Description                                              | Data Source              | Target                |
|-----------|----------------------------------|----------------------------------------------------------|--------------------------|-----------------------|
| M-001     | Mean Time to Detect (MTTD)       | Time elapsed from anomaly occurrence to first alert      | SIEM (Better Stack)      | < 15 minutes          |
| M-002     | False Positive Rate (FPR)        | % of alerts triaged as benign                            | Analyst triage logs      | ≤ 5%                  |
| M-003     | True Positive Rate (TPR)         | % of alerts confirmed as actual security incidents       | Incident tracker         | ≥ 95%                 |
| M-004     | Tier-1 Detection Rate            | % of incidents initially identified by Tier-1 analysts   | Case management system   | ≥ 70%                 |
| M-005     | Log Source Coverage              | % of critical systems feeding logs into the SIEM         | SIEM inventory report    | 100% of core systems  |
| M-006     | Feedback Closure Rate            | % of tuning tickets resolved within SLA (30 days)        | Jira “DETECT” project    | ≥ 90%                 |

---

## 3. Dashboards & Reports

- **Executive Dashboard**  
  - MTTD, TPR, FPR trends (monthly/quarterly)  
  - SLA attainment and high-level incident counts  

- **Operational Dashboard**  
  - Real-time alerts by rule ID and severity  
  - Log source health and coverage indicators  
  - Tier-1 vs. Tier-2 detection volumes  

- **Analyst Triage Report**  
  - Weekly summary of true vs. false positives  
  - Breakdown by detection rule and responder  

---

## 4. Review Cadence & Stakeholders

| Cadence    | Participants                         | Output                              |
|------------|--------------------------------------|-------------------------------------|
| Weekly     | Security Analysts, Tier-1 Leads      | Triage summary and tuning requests  |
| Monthly    | Detection Engineers, Library IT      | Metrics deep-dive and rule updates  |
| Quarterly  | IR Lead, CISO, Library CIO           | Trend analysis and roadmap review   |

---

## 5. Action & Escalation

- If MTTD ≥ 15 min for two consecutive weeks, initiate a rule-tuning sprint.  
- If FPR > 5% for one month, conduct a false-positive review workshop.  
- If Log Source Coverage < 100%, escalate to Library IT for remediation.  
- If Feedback Closure Rate < 90%, report to IR Lead for resource reallocation.  

---

## 6. Change Log

| Version | Date       | Author   | Description                              |
|---------|------------|----------|------------------------------------------|
| 1.0     | 2025-07-26 | Kishore  | Initial metrics and reporting plan       |
| 1.1     | 2025-08-15 | Kishore  | Added Tier-1 Detection Rate and coverage |
| 1.2     | 2025-10-01 | Kishore  | Refined escalation thresholds            |
