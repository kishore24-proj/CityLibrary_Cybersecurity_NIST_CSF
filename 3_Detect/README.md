# 3_Detect

## Purpose

This directory contains the playbooks, guides, and processes you need to detect security events across our environment. It aligns with the NIST Cybersecurity Framework’s Detect function (DE).

## Scope

All activities and documentation related to:

- Collecting and reviewing logs  
- Network and host-based monitoring  
- Vulnerability scanning  
- Intrusion detection and alerting  
- Threat intelligence ingestion  

## Folder Contents

| File                                  | Description                                                                 | NIST CSF Subcategory      |
|---------------------------------------|-----------------------------------------------------------------------------|---------------------------|
| README.md                             | Overview of this folder, how it maps to CSF Detect, and how to use these docs | —                         |
| Logging_and_Monitoring_Plan.md        | Defines which log sources we collect, retention periods, review cadence     | DE.CM-1, DE.CM-2, DE.CM-3  |
| SIEM_Deployment_Guide.md              | Instructions for installing, configuring, and tuning our SIEM platform      | DE.CM-4                   |
| Vulnerability_Scanning_Playbook.md    | Schedules, tool configurations, and escalation paths for vulnerability scans| DE.CM-8                   |
| Intrusion_Detection_Playbook.md       | Network/host IDS/IPS rules, alert thresholds, triage and escalation steps   | DE.CM-1, DE.CM-4          |
| Threat_Intelligence_Process.md        | Sources, ingestion pipeline, enrichment, and integration with monitoring    | DE.TE-1, DE.TE-2, DE.TE-3  |

## How to Use

1. Review the Logging and Monitoring Plan to understand which events we collect.  
2. Follow the SIEM Deployment Guide to ensure your data feeds are onboarded and alerts are tuned.  
3. Execute Vulnerability Scanning as per the playbook schedule.  
4. Monitor IDS/IPS alerts and follow escalation steps in the Intrusion Detection Playbook.  
5. Keep the Threat Intelligence Process updated with new feeds and integrate them into your SIEM or monitoring tools.  

## Contributing

- When you add a new detection capability (e.g., a new log source or sensor), update the Logging_and_Monitoring_Plan.md.  
- If you onboard a new threat feed, document it in Threat_Intelligence_Process.md.  
- For any changes, submit a pull request with “3_Detect” in the title for easy tracking.

---
