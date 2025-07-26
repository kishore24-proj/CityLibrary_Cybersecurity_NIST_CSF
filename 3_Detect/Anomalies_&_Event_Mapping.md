# Anomalies and Event Mapping

## 1. Purpose and Scope

Define the anomalies and events your detection pipeline will surface.  
Explain which systems, log sources, and use-cases this document covers.

---

## 2. Event Sources

List and describe each telemetry stream:

- **Authentication Logs**  
  Source: Active Directory, LDAP, cloud IAM  
  Captures: logins, logouts, MFA failures  
- **Network Flows**  
  Source: NetFlow, VPC Flow Logs, firewall logs  
  Captures: source/destination IPs, ports, protocols  
- **Endpoint Telemetry**  
  Source: EDR agents, OS audit logs  
  Captures: process launches, file access, registry changes  
- **Application Logs**  
  Source: web server, API gateway, custom app logs  
  Captures: request paths, payload size, error messages  

---

## 3. Anomaly Definitions

Describe each anomaly condition and how it’s detected:

| Anomaly ID            | Definition                                                                 | Detection Logic                     |
|-----------------------|----------------------------------------------------------------------------|-------------------------------------|
| AE-001: Brute Force   | Rapid successive failed logins from one IP                               | > 10 failed auths in 2 min from same IP |
| AE-002: Data Exfil    | Large outbound transfer to unusual destination                           | > 500 MB out to external IP not seen before |
| AE-003: Privilege Esc | Unauthorized privilege escalation event                                  | Windows event 4672 (admin group added) |
| AE-004: Beaconing     | Regular, low-volume callbacks indicating C2                             | > 5 DNS queries to same domain every 5 min |

---

## 4. Event Correlation & Enrichment

Provide examples of how you’ll tie multiple signals together:

1. **Multi-Stage Intrusion**  
   - Failed logins → New user creation → High-privilege API calls  
   - Correlate auth logs with directory change events and API audit trails  
2. **Data Exfiltration via DNS Tunneling**  
   - Unusually large DNS request sizes + repeated queries to same external domain  
   - Enrich DNS logs with threat intelligence feeds for known C2 domains  
3. **Lateral Movement Detection**  
   - Remote SMB access + Windows Admin share usage + PSExec process spawn  
   - Combine network flow logs with EDR process trees  

---

## 5. Prioritization & Response Mapping

Assign each anomaly a priority and link to runbook:

| Anomaly ID  | Severity | Runbook Reference          |
|-------------|----------|----------------------------|
| AE-001      | High     | `3_Respond/brute_force.md` |
| AE-002      | Critical | `3_Respond/data_exfil.md`  |
| AE-003      | Medium   | `3_Respond/priv_esc.md`    |
| AE-004      | Low      | `3_Respond/beaconing.md`   |

---

## 6. Change Log

Track updates to this document:

| Date       | Author   | Change Description               |
|------------|----------|----------------------------------|
| 2025-07-26 | Kishore  | Initial anomaly & event mapping  |
|            |          |                                  |
