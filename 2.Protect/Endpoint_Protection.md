# Endpoint Protection Overview

## Purpose

Ensure all library-owned endpoints are protected against malware, unauthorized access, and data leakage.

## Scope

Covers all desktops, laptops, self-checkout kiosks, tablets, and mobile devices owned or managed by the City Library.

## Tools & Technologies

Antivirus/Antimalware  
  Sophos Endpoint Protection on Windows and macOS  
Full-Disk Encryption  
  BitLocker (Windows)  
  FileVault (macOS)  
Mobile Device Management  
  Microsoft Intune for staff laptops and tablets  
Web Filtering  
  DNS-level filtering for malicious sites

## Patch Management

 Weekly automated OS and application updates via WSUS (Windows) and Munki (macOS)  
 Critical security patches deployed within 24 hours of vendor release  
 Monthly review of patch compliance reports

## Device Hardening

 Disable all unused USB ports, Bluetooth, and Wi-Fi interfaces when not required  
 Enforce automatic screen lock after 10 minutes of inactivity  
 Remove legacy or unsupported software from endpoints  
 Enforce least-privilege local user accounts (no admin rights for standard users)

## Monitoring & Response

 Endpoint detection & response (EDR) alerts fed into central SIEM  
 Daily review of high-severity endpoint alerts by IT Security  
 Rapid containment playbook for infected or compromised devices
