# Detection Testing and Validation Plan

## 1. Purpose & Scope

Describe why and what we’re testing in Detect (DE.AE & DE.DP).  
Define which rules, processes, and metrics this plan covers.

---

## 2. Test Environment

- SIEM/Test SIEM instance URL  
- Log generators and replay tools (e.g., [Sigma tools], custom scripts)  
- Metrics mocker (e.g., Prometheus pushgateway)  
- Version of detection_rules.yaml under test  

---

## 3. Test Scenarios & Data

| Scenario ID | Rule / Process             | Description                                      | Test Data Source                      |
|-------------|----------------------------|--------------------------------------------------|---------------------------------------|
| TS-001      | AE-001: Brute Force        | 12 failed logins in 2 minutes                    | `tests/data/bruteforce_events.json`   |
| TS-002      | AE-002: Data Exfil         | 600 MB outbound to new IP                        | `tests/data/data_exfil_logs.log`      |
| TS-003      | Rule Deployment Process    | CI/CD pipeline promotes changes to test SIEM     | N/A (simulate PR → merge → deploy)    |
| TS-004      | Alert Triage Workflow      | Analyst escalates a true positive correctly      | Manual walk-through using mock alert  |

---

## 4. Acceptance Criteria

- Each detection rule fires within expected timeframe.  
- Alerts generated contain required context fields (timestamp, host, user, rule_id).  
- No false positives in negative-test datasets.  
- CI/CD job marks pass/fail per rule.

---

## 5. Test Automation

- Unit tests: `tests/detect_rules_test.py` (pytest / bats)  
- Integration tests: log-replay scripts in `tests/integration/`  
- Smoke tests: quick-run suite on every PR

---

## 6. Schedule & Maintenance

- Run full test suite on every merge to `main`.  
- Nightly regression tests in staging.  
- Quarterly review of test data (rotate, refresh, expand).

---

## 7. Reporting

- Test results pushed to dashboard (e.g., GitHub Actions, Jenkins).  
- Weekly summary emailed to SecOps & Dev teams.  
- Monthly meeting to review failures, flakiness, and data gaps.

---

## 8. Change Log

| Date       | Author  | Change Description                       |
|------------|---------|------------------------------------------|
| 2025-07-26 | Kishore | Initial detection testing plan created   |
