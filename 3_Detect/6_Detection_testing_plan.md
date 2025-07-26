##Library Detection Testing Plan

### Purpose & Scope

This document defines the test scenarios, methods, and acceptance criteria used to validate all library detection rules, anomaly models, and integrations before they are promoted to production.

### File Location

`3_Detect/tests/Library_Detection_Testing_Plan.md`

---

### 1. Test Environment Setup

- Provision a dedicated test SIEM or streaming pipeline instance.  
- Deploy the latest rule and model artifacts under test.  
- Configure a replay tool or synthetic data generator for input streams.  
- Ensure logging, monitoring, and metric collection are enabled.

---

### 2. Test Categories

- Threshold Tests (e.g., login failures, data volume)  
- Behavioral Model Validation (anomaly scoring)  
- Schedule‐Based Tests (after‐hours access)  
- Novelty Detection Tests (new device fingerprints)  
- End‐to‐End Integration Tests (alert lifecycle)

---

### 3. Test Cases

| Test ID | Category        | Description                                      | Input Data                            | Expected Outcome                                             |
|---------|-----------------|--------------------------------------------------|---------------------------------------|--------------------------------------------------------------|
| TC-001  | Threshold       | Excessive login failures                         | 6 failed logins within 10 minutes     | LD-RULE-001 alert; severity = medium                         |
| TC-002  | Threshold       | Large data download                              | 600 MB download in one session        | LD-RULE-002 alert; severity = high                           |
| TC-003  | Schedule        | After‐hours system access                        | Access event at 23:15 local time      | LD-RULE-003 alert; severity = low                            |
| TC-004  | Novelty         | Login from unseen device                         | New IP and user-agent per user        | LD-RULE-004 alert; severity = medium                         |
| TC-005  | Model           | High cumulative anomaly score                    | Features normalized to score ≥ 0.75   | Alert with anomaly_score and triggered_features payload      |
| TC-006  | Integration     | Combined anomalies triggering consolidated alert | Sequence of TC-001 & TC-005 events    | Single consolidated alert with full context and metadata     |

---

### 4. Execution & Reporting

1. Load test streams into the replay bus.  
2. Activate detection pipeline and monitor alert outputs.  
3. Log actual results against expected in the “Test Results” template.  
4. File failures or discrepancies as tickets in Jira “DETECT-TEST”.  
5. Iterate: adjust rules/models, redeploy, and re-run tests until all pass.

---

### 5. Maintenance & Review

- Conduct quarterly reviews of test coverage alongside rule updates.  
- Archive retired or deprecated test cases under `3_Detect/tests/archives/`.  
- Version‐control any changes to this plan and capture updates in the change log.

---

### 6. Change Log

| Date       | Author   | Description                          |
|------------|----------|--------------------------------------|
| 2025-07-26 | Kishore  | Initial Library Detection Testing Plan created |

---
