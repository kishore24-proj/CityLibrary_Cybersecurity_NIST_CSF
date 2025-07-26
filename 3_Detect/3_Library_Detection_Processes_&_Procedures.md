# Detection Processes & Procedures: Library

## 1. Daily Log Review

- Review ILS & OPAC authentication and checkout logs  
  - Look for failed logins, admin console access, rapid succession of searches  
- Scan EDR/antivirus dashboards for new malware alerts on endpoints  
- Check firewall & Wi-Fi controller logs for blocked sessions or unusual SSID associations  
- Correlate badge reader and CCTV summary reports for out-of-hours entries  
- Document findings in the SIEM ticketing queue  

## 2. Real-Time Monitoring

- SIEM Dashboards  
  - OPAC error spike widget (threshold: >100 errors/hr)  
  - Self-checkout failure rate (threshold: ≥5 failures/5 min)  
  - Network anomaly stream (port scans, large file transfers)  
- Alert Channels  
  - EDR alerts via Teams channel “Library-EDR-Alerts”  
  - SIEM high-severity notifications via SMS to on-call analyst  
- Physical-Digital Correlation  
  - Automatic linkage of badge-swipe anomalies with OPAC activity  
  - CCTV thumbnail snapshots on critical alerts  

## 3. Triage & Escalation Workflow

1. Tier-1 Analyst  
   - Validate alert details and check for known false positives  
   - Triage severity (Low/Medium/High) against Incident Classification matrix  
   - Add context: user identity, device, location  
2. Incident Response Lead  
   - Confirm escalation for High or Critical events  
   - Assign to IR team member or relevant technical owner  
   - Initiate Incident Response Plan if necessary  
3. Technical Owners  
   - Network Admin for connectivity issues  
   - Systems Engineer for ILS/OPAC events  
   - Facilities Team for physical-security anomalies  
4. Communications & Legal  
   - Engage Communications for patron notifications on PII exposure  
   - Inform Legal/Compliance for regulatory reporting  

## 4. Investigation Procedures

- Collect relevant logs and forensic snapshots  
  - Export EDR process trees, network captures, database audit trail  
- Perform user validation  
  - Confirm badge swipe history, interview staff or patron if required  
- Cross-check external threat intelligence  
  - Look up IOC in regional CERT feeds or vendor bulletins  
- Document each step in the SIEM ticket and update status  

## 5. Documentation & Handover

- Record timelines: detection, triage, containment actions  
- Update playbook with any new IOCs or thresholds  
- After resolution, produce a concise incident summary  
  - Include root cause, impact assessment, and recommended improvements  
- Schedule a lessons-learned review with stakeholders  

---
