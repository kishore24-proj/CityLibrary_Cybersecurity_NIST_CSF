# Anomalies & Event Mapping

## 1. Purpose & Scope

This document defines how we classify and map detected anomalies to underlying event sources. It ensures every anomaly use case is traceable to one or more log events, enabling clear rule authoring, tuning, and investigation workflows.

---

## 2. Anomaly Definitions & Event Mapping

| Anomaly ID | Name                              | Description                                                 | Event Source                    | Key Fields / Indicators               | Detection Rule ID | Severity |
|------------|-----------------------------------|-------------------------------------------------------------|---------------------------------|---------------------------------------|-------------------|----------|
| A-001      | Unusual Login Geography           | User logs in from a location not seen in baseline history   | Windows Security Event (4624), Cloud Auth Logs | user.name, src.ip, geo.location     | R-101             | High     |
| A-002      | Multiple Failed Logon Attempts    | Excessive failed logins over short interval                  | Windows Security Event (4625), SSHD Logs         | user.name, src.ip, failure.count    | R-102             | Medium   |
| A-003      | New Administrative Account Created| Creation of a user with privileged group membership         | Windows Security Event (4720 & 4732), LDAP Logs  | user.name, group.name               | R-103             | High     |
| A-004      | Suspicious Process Spawn          | High-risk executable launched by non-standard parent process | Sysmon
