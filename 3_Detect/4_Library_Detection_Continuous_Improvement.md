# Continuous Improvement: Library Detection

## 1. Purpose & Scope

This plan ensures that detection rules, processes, and metrics evolve based on real incidents, performance data, and stakeholder feedback. It covers all library detection artifacts in `3_Detect/`, including anomaly definitions, rules, monitoring pipelines, and reporting.

---

## 2. Feedback Sources

- Incident post-mortems (malware outbreaks, data exfiltration events)  
- Alert performance metrics (MTTD, TPR, FPR) from SIEM/Better Stack dashboards  
- Librarian and patron reports (e.g., false positives on self-checkout kiosks)  
- Facilities team insights (physical-digital correlation anomalies)  
- Regional CERT advisories on library-sector threats  

---

## 3. Continuous Improvement Workflow

1. Collect Feedback  
   - Aggregate post-mortem action items and analyst tuning requests  
   - Pull monthly detection metrics and incident summaries  
2. Prioritize Updates  
   - Score by patron impact (service availability × data sensitivity)  
   - Estimate effort for rule/process changes  
3. Implement Enhancements  
   - Adjust thresholds in `Library_Detection_Rules_Library.yaml`  
   - Refine procedures in `Library_Detection_Processes_&_Procedures.md`  
4. Validate Changes  
   - Execute scenarios in `Library_Detection_Testing_Plan.md`  
   - Confirm metrics improvement without regression  
5. Deploy & Document  
   - Version control commits and update change logs  
   - Communicate updates to library IT, security analysts, and facilities  
6. Review Effectiveness  
   - Re-measure key metrics after 30 days  
   - Close feedback loop in weekly tuning meeting  

---

## 4. Roles & Responsibilities

- Detection Engineers: apply, test, and document rule/process updates  
- Security Analysts: validate in triage and report new patterns  
- Library IT: deploy pipeline changes and maintain logging infrastructure  
- Facilities Team: confirm physical feed quality and correlate incidents  
- IR Lead: chair tuning meetings and ensure follow-through on action items  

---

## 5. Cadence & Schedule

| Cadence   | Activity                                    | Owner             |
|-----------|---------------------------------------------|-------------------|
| Weekly    | Tuning meeting to review analyst feedback   | IR Lead           |
| Monthly   | Metrics & post-mortem summary               | Detection Engineers |
| Quarterly | Tabletop exercise with library & facilities | Security Analysts |

---

## 6. Tooling & Tracking

- Issue tracker (e.g., Jira “DETECT” project) for feedback tickets  
- Version control audit trail for all `3_Detect/` artifacts  
- Dashboard annotations in Better Stack for rollout dates  

---

## 7. Change Log

| Date       | Author   | Description                                  |
|------------|----------|----------------------------------------------|
| 2025-07-26 | Kishore  | Initial continuous improvement plan created  |

## 8. Key Performance Indicators

This section defines the metrics that will gauge the success of the continuous improvement process. Each KPI is measured monthly, tracked on dashboards, and reviewed during tuning meetings.

- Mean Time to Detect (MTTD): average time from threat emergence to alert  
- Mean Time to Respond (MTTR): average time from alert to containment action  
- True Positive Rate (TPR): proportion of alerts that correspond to real incidents  
- False Positive Rate (FPR): proportion of alerts deemed benign after triage  
- Feedback Closure Rate: percentage of feedback tickets resolved within SLA  
- Rule Change Adoption: ratio of deployed changes that pass validation tests  

| KPI                     | Target Threshold     | Measurement Tool        |
|-------------------------|----------------------|-------------------------|
| MTTD                    | ≤ 15 minutes         | SIEM dashboard          |
| MTTR                    | ≤ 30 minutes         | Incident tracker        |
| TPR                     | ≥ 95%                | Detection metrics report|
| FPR                     | ≤ 5%                 | Analyst triage logs     |
| Feedback Closure Rate   | ≥ 90% within 30 days | Jira “DETECT” project   |
| Rule Change Adoption    | ≥ 98% pass rate      | Automated test suite    |

---

## 9. Risk Considerations

Identifying and mitigating risks ensures the continuous improvement loop remains effective and resilient.

- Data Drift: logging schema changes or library system upgrades may invalidate rules  
- Over-Tuning: overly aggressive threshold adjustments can increase FPR or blind spots  
- Resource Constraints: limited analyst or engineering capacity may delay updates  
- Dependency Failures: CI/CD pipeline outages can stall deployments and testing  
- Threat Evolution: novel attack techniques may outpace existing detection logic  

For each risk, assign an owner, document mitigation steps in the risk register, and review quarterly.

---

## 10. Appendix: Templates & Resources

| Appendix | Name                          | Location                                           |
|----------|-------------------------------|----------------------------------------------------|
| A        | Tuning Ticket Template        | docs/templates/tuning_ticket.md                    |
| B        | Post-Mortem Report Template  | docs/templates/postmortem_report.md                |
| C        | Detection Testing Checklist   | docs/templates/detection_testing_checklist.xlsx    |
| D        | Dashboard Setup Guide         | docs/guides/betterstack_dashboard_setup.md         |

