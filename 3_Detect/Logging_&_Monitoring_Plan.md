# Logging and Monitoring Plan

## Purpose

This document defines what events we collect, how we store them, and the processes we follow to turn raw log data into actionable alerts.

## Scope

Covers all log sources across on-premises, cloud, and endpoint systems. Applies to:

- Network devices (firewalls, routers, switches)  
- Operating systems and servers  
- Critical applications and databases  
- Endpoint agents (EDR/AV)  
- Cloud infrastructure and services  

---

## Log Sources & Retention

| Source                       | Description                                  | Owner               | Collection Frequency | Retention Period |
|------------------------------|----------------------------------------------|---------------------|----------------------|------------------|
| Firewall                     | Allow/deny traffic, configuration changes    | Network Team        | Real-time            | 1 year           |
| Windows/Linux Servers        | System events, authentication, application   | Server Operations   | Real-time            | 1 year           |
| Endpoint Detection & Response| Process creation, suspicious behaviors       | SecOps              | Near real-time       | 90 days          |
| Cloud Audit Logs             | API calls, resource changes                  | Cloud Team          | Real-time            | 1 year           |
| Database Activity Logs       | Queries, failed logons                       | DB Admins           | Daily batch          | 180 days         |

---

## Roles & Responsibilities

- SecOps Team  
  - Onboard and validate log sources  
  - Tune alert rules, investigate anomalies  

- Network Team  
  - Ensure network devices forward logs  
  - Review firewall change logs weekly  

- Server Operations  
  - Verify OS and application logs are complete  
  - Patch log-forwarding agents  

- Cloud Team  
  - Configure cloud services to forward audit logs  
  - Monitor quota and ingestion costs  

---

## Monitoring & Alerting

1. Ingest logs into SIEM within 5 minutes of generation.  
2. Use out-of-the-box and custom correlation rules for:  
   - Brute-force or lateral-movement patterns  
   - Privilege-escalation attempts  
   - Data exfiltration signatures  
3. Assign a severity (Low, Medium, High) to each alert based on impact.  
4. Route High-severity alerts to the on-call SecOps Slack channel and ticketing queue.  

---

## Review & Escalation

- Daily triage meetings at 09:00 EDT to review Medium/High alerts.  
- Escalation path:  
  1. SecOps Analyst → 2. Incident Response Lead → 3. CISO  
- Document false positives to revise alert tuning.

---

## Metrics & KPIs

- Mean Time to Detect (MTTD) – target < 30 minutes  
- Alert Volume by Severity – track monthly trends  
- False Positive Rate – target < 20%  
- Log Coverage % – target 100% of critical assets  

---

## Revision History

| Version | Date       | Author       | Changes                          |
|---------|------------|--------------|----------------------------------|
| 1.0     | 2025-07-26 | SecOps Team  | Initial Logging and Monitoring Plan |
