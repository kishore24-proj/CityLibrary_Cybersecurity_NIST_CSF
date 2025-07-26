# Anomalies & Event Mapping: Library

## 1. User Behavior Anomalies

- After-hours OPAC query surge  
  - Data Source: OPAC application logs  
  - Indicator: >100 searches in 30 min outside business hours  
  - Severity: Medium  
  - Initial Response: Verify user badge swipe; if none, trigger alert  

- Repeated self-checkout failures  
  - Data Source: Self-checkout kiosk logs  
  - Indicator: ≥5 failed scans of library card within 5 min  
  - Severity: Low  
  - Initial Response: Lock kiosk UI; dispatch staff to assist  

- Unusual staff credential use  
  - Data Source: Directory service / EDR logs  
  - Indicator: Staff account accessing admin console from public Wi-Fi  
  - Severity: High  
  - Initial Response: Lock account; confirm identity via phone  

## 2. System & Network Anomalies

- Bulk download from digital archives  
  - Data Source: File server / web server logs  
  - Indicator: ≥50 GB transferred to a single IP in 1 hr  
  - Severity: High  
  - Initial Response: Throttle connection; investigate user session  

- Firewall port-scan pattern  
  - Data Source: Firewall logs  
  - Indicator: >100 different ports probed by one external IP in 10 min  
  - Severity: Medium  
  - Initial Response: Blacklist IP; escalate to network team  

- Rogue device on library VLAN  
  - Data Source: Network controller / NAC logs  
  - Indicator: New MAC address not in asset inventory  
  - Severity: Medium  
  - Initial Response: Quarantine on guest network; notify IT  

## 3. Physical-Digital Correlation

| Event Source            | Anomaly                                | Correlated Signal                  | Response Action                                |
|-------------------------|----------------------------------------|------------------------------------|------------------------------------------------|
| CCTV door sensor       | Entry after hours                      | OPAC login attempts during closed period | Verify badge logs; if mismatch, alert security |
| Badge reader           | Tailgating event                       | Multiple badge scans in same minute | Review CCTV clip; notify facilities             |
| RFID gate controller   | Gate held open >30 sec                 | High self-checkout failures        | Lock gate; dispatch on-floor staff              |

## 4. Response Prioritization

1. High: Potential data exfiltration or credential compromise  
2. Medium: Network reconnaissance or atypical user behavior  
3. Low: Minor kiosk issues or single-user anomalies  

---
