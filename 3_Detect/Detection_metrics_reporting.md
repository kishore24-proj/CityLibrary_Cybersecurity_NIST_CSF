# Detection Metrics & Reporting Plan

## 1. Purpose & Scope

Define how you’ll measure, report, and review the effectiveness of your Detect-phase controls.  
Specify which detection rules, anomalies, and processes this covers.

---

## 2. Metrics Definitions

| Metric ID | Name                           | Description                                              | Data Source                 |
|-----------|--------------------------------|----------------------------------------------------------|-----------------------------|
| M-001     | Mean Time to Detect (MTTD)     | Average time from event generation to alert delivery     | SIEM alert timestamps       |
| M-002     | True Positive Rate (TPR)       | % of alerts that correctly represent real incidents      | Incident tracker            |
| M-003     | False Positive Rate (FPR)      | % of alerts deemed benign after triage                   | Triage logs                 |
| M-004     | Alert Coverage                 | % of critical use-cases with at least one detection rule | Anomalies & event mapping   |

---

## 3. Dashboards & Reports

- **Executive Dashboard**  
  - High-level MTTD, TPR, FPR trends (monthly/quarterly)  
  - SLA/SLO attainment overview  

- **Operational Dashboard**  
  - Real-time alerts by severity and rule ID  
  - Quarterly heatmap of high-frequency anomalies  

- **Triage Report**  
  - Weekly summary of true vs. false positives  
  - Breakdown by detection rule and analyst  

---

## 4. Review Cadence & Stakeholders

| Cadence    | Participants                         | Output                              |
|------------|--------------------------------------|-------------------------------------|
| Weekly     | SecOps Lead, Detection Engineers     | Alert volume & triage summary       |
| Monthly    | Security Manager, Compliance         | SLA/SLO attainment report           |
| Quarterly  | CIO, CISO, DevOps, Risk Management   | Trend analysis & improvement roadmap|

---

## 5. Action & Escalation

- If MTTD exceeds threshold, trigger a process-improvement meeting.  
- If FPR > 10% for two consecutive months, initiate rule-tuning sprint.  
- SLA breaches escalate to CISO for risk assessment.  

---

## 6. Change Log

| Date       | Author   | Description                             |
|------------|----------|-----------------------------------------|
| 2025-07-26 | Kishore  | Initial metrics & reporting plan created|

