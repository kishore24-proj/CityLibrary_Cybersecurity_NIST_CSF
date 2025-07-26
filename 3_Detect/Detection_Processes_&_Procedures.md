# Detection Processes and Procedures

## 1. Purpose and Scope

Describe why these processes exist and what systems, teams, and threat categories they cover.

---

## 2. Roles and Responsibilities

- Detection Engineers: author and tune detection logic  
- Security Analysts: triage alerts and escalate incidents  
- DevOps/Platform Teams: onboard new services into monitoring pipelines  
- Compliance Team: ensure procedures meet regulatory requirements  

---

## 3. Process Workflow

1. Rule Development  
   - Draft new detection logic based on threat intelligence  
   - Peer-review rule criteria and thresholds  
2. Testing & Validation  
   - Run simulated events or use a test SIEM instance  
   - Verify alerts fire correctly and contain actionable context  
3. Deployment  
   - Promote rules through CI/CD into production  
   - Tag versions and maintain changelog  
4. Alert Triage  
   - Security Analysts investigate and classify alerts  
   - Document false positives and update rules  
5. Continuous Review  
   - Monthly tuning sessions to retire stale alerts  
   - Quarterly red-team exercises to validate coverage  

---

## 4. Review and Improvement Cycle

- Weekly demo of new or updated detections  
- Monthly metrics review (alert volume, mean time to detect)  
- Annual tabletop exercises to stress-test procedures  

---

## 5. Metrics and KPIs

| Metric                          | Target        | Frequency  |
|---------------------------------|---------------|------------|
| Mean Time to Detect (MTTD)      | < 15 minutes  | Continuous |
| False Positive Rate             | < 5%          | Monthly    |
| Coverage of High-Risk Scenarios | 100%          | Quarterly  |

---

## 6. References

- NIST CSF v1.1 – Detect Function (DE.DP)  
- Company Security Policy Doc #SEC-1234  
- Incident Response Runbooks in `3_Respond/`
