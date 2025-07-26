# Logging & Monitoring Plan: Library

## 1. Overview

Describe the purpose of logging and monitoring in your library, tying it to security, compliance, and operational visibility.

## 2. Log Sources

- ILS & OPAC application logs  
- EDR/antivirus on all endpoints (public terminals, staff workstations)  
- Network devices (firewalls, routers, Wi-Fi controllers)  
- Physical security (CCTV access logs, badge readers)  
- Cloud services (email/M365 audit logs, SaaS e-resource portals)  

## 3. Collection & Aggregation

- Centralize logs into a SIEM or log management platform  
- Use agents, syslog, API pulls, and secure file transfer  
- Normalize timestamps and essential fields for correlation  

## 4. Storage & Retention

- Define retention periods by log type (e.g., 1 year for SIEM, 30 days for CCTV)  
- Ensure write-once, read-many (WORM) or append-only storage where required  
- Outline archival process and offsite backups  

## 5. Access & Analysis

- Role-based access controls:  
  - Tier-1 analysts view/acknowledge alerts  
  - IR Lead and Senior Engineers have full query rights  
- Establish dashboards for key metrics (MTTD, unusual OPAC queries, badge anomalies)  

## 6. Review Cadence

- Daily: automated alerts & high-severity event review  
- Weekly: analyst triage of medium-severity events  
- Monthly: SIEM health check, log completeness, rule firing trends  

## 7. Roles & Responsibilities

- Library IT: maintain log collectors and retention policies  
- Security Analyst: tune alerts, investigate anomalies  
- Facilities Team: ensure physical logs (CCTV, badge) feed into SIEM  
- IR Lead: oversee monitoring maturity and run quarterly audits  

## 8. Tooling & Integrations

- Better Stack: a modern, SQL-compatible structured log management platform enabling petabyte-scale search, anomaly detection, and real-time collaboration  

---
