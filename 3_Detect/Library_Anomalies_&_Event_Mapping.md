# Anomalies & Event Mapping: Library

## 1. User Behavior Anomalies
- After‐hours OPAC queries surging  
- Self‐checkout kiosk repeated loan attempts  

## 2. System Events
- Unusual spikes in digital archives downloads  
- Unauthorized config changes on ILS server  

## 3. Physical‐Digital Correlation
| Event Source       | Anomaly                             | Response Trigger        |
|--------------------|-------------------------------------|-------------------------|
| CCTV door sensor   | Patron entry during closed hours    | Verify badge log       |
| Self‐checkout logs | Multiple failed scans in a row      | Lock kiosk & alert IR  |
