# 4_Respond: Forensic Analysis Guidelines (Library)

## 1. Purpose & Scope

This document prescribes standardized procedures for collecting, preserving, and analyzing digital and physical evidence during library security incidents. It ensures legal defensibility, chain-of-custody integrity, and reproducible analysis.

---

## 2. Key Roles & Responsibilities

| Role                     | Responsibility                                                   |
|--------------------------|------------------------------------------------------------------|
| Forensic Lead            | Oversees evidence collection, chain-of-custody, and analysis        |
| IR Manager               | Authorizes forensic actions, ensures legal/compliance alignment    |
| SOC Analyst              | Identifies candidate hosts, network segments, log sources          |
| IT Support/Facilities    | Provides system access, powers down devices, secures physical media |
| Legal/Privacy Officer    | Advises on warrants, patron PII, regulatory notifications          |

---

## 3. Legal & Privacy Considerations

- Confirm authorization (incident ticket, IR Manager sign-off).  
- Involve Legal/Privacy for any patron PII or regulated data.  
- Adhere to applicable Canadian privacy laws and library policy.

---

## 4. Evidence Preservation

1. Document initial incident facts (time, affected systems, custodian).  
2. Photograph device and workspace for context.  
3. Isolate systems from network without powering off if live response is required.  
4. Create forensic images of storage media (disk, USB), using write-blockers.  
5. Capture volatile memory (RAM) using trusted tools.  
6. Export relevant logs (EDR, application, authentication, CCTV, badge readers).

---

## 5. Chain-of-Custody

| Step                     | Owner             | Artifact                   | Location                |
|--------------------------|-------------------|----------------------------|-------------------------|
| Collection               | Forensic Lead     | Media images, log exports  | Evidence locker         |
| Transfer                 | IT Support        | Physical media             | Secured transport case  |
| Receipt                  | Forensic Lead     | Digital hash values        | Evidence catalog        |
| Analysis                 | Forensic Analyst  | Working copies              | Secure analysis server  |
| Storage                  | IR Manager        | Original media, reports    | Long-term archive vault |

Record all hand-offs with date, time, signatures, and hash values.

---

## 6. Analysis Procedures

- Mount images in read-only mode; verify hashes.  
- Timeline reconstruction:  
  * Parse OS logs (Windows Event, syslog), application and network logs.  
  * Correlate with badge/CCTV timestamps.  
- Memory analysis:  
  * Extract process list, network connections, loaded modules.  
  * Identify in-memory malware or unauthorized tools.  
- Malware triage:  
  * Isolate suspicious binaries; perform static/dynamic analysis in sandbox.  
- Document findings with screenshots, query outputs, and annotated artifacts.

---

## 7. Tools & Environment

- Hardware: write-blockers, Faraday bags, portable evidence kits.  
- Software: FTK Imager, Autopsy/Sleuth Kit, Volatility, Wireshark, YARA.  
- Logging: centralized SIEM exports, EDR console, CCTV/VMS archives.  
- Documentation: standardized evidence intake and analysis templates in Confluence.

---

## 8. Reporting & Handoff
1. Compile Forensic Analysis Report with:  
   - Executive summary, scope, methodology  
   - Evidence inventory and chain-of-custody log  
   - Detailed findings and timelines  
   - Conclusions and recommended remediation  
2. Submit report to IR Manager and Legal/Privacy for review.  
3. Archive all original media and analysis outputs securely.

---

## 9. Review Cadence & Change Log

| Version | Date       | Author        | Description                            |
|---------|------------|---------------|----------------------------------------|
| 1.0     | 2025-07-27 | Kishore       | Initial forensic guidelines for library|
| 1.1     | 2025-08-20 | Kishore       | Added CCTV and badge reader procedures|


