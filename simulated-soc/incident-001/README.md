# SIMULATION — SOC Incident 001

## Multi-Endpoint Phishing & Malicious PowerShell Investigation

**Date:** September 14, 2026  
**Role:** Junior Cybersecurity Analyst — Co-op *(Simulation)*  
**Environment:** Southwestern Ontario Technology & Security Services (SOTS) *(Fictional)*  
**Incident Severity:** HIGH  
**Incident Type:** Phishing / Malicious Office Document / PowerShell / C2

> **SIMULATION NOTICE:** This is a fictional cybersecurity career exercise. The organizations, users, systems, IP addresses, hashes, and incident data are fictional and must not be represented as real employment or a real security incident.

---

## Incident Summary

A simulated phishing campaign targeted 11 employees with a malicious Microsoft Office `.docm` document.

The investigation began with an EDR alert for suspicious PowerShell activity and expanded into a multi-endpoint investigation using endpoint, network, DNS, email, authentication, and file telemetry.

### Key Findings

- **11 employees** received the phishing email.
- **3 endpoints** showed confirmed malicious execution.
- **1 endpoint** was exposed but showed no evidence of compromise.
- Malicious PowerShell activity was identified.
- A suspicious DLL was executed through `rundll32.exe`.
- Multiple systems communicated with the same external infrastructure.
- An LSASS access attempt was observed and denied.
- Sensitive documents were accessed on one compromised endpoint.
- Potential data exfiltration was investigated but **not confirmed**.

---

## Attack Chain

**Phishing Email → Malicious Office Document → Macro Execution → PowerShell → Remote Payload Download → `update.dll` → `rundll32.exe` → C2 Communication**

---

## Key Indicators

| Indicator | Value |
|---|---|
| Malicious document | `Invoice_September_2026.docm` |
| Document SHA-256 | `7f3c...91a2` |
| Malicious DLL | `update.dll` |
| DLL SHA-256 | `91ab...72ef` |
| Malicious domain | `invoice-update[.]com` |
| Malicious IP | `185.XX.XX.47` |

---

## Endpoint Assessment

### 🔴 SWM-FIN-WS23

**Status:** Confirmed compromised

- Malicious Office document opened
- Macro enabled
- PowerShell executed
- External C2 communication
- `update.dll` executed through `rundll32.exe`
- LSASS access attempted and denied
- Endpoint isolated

### 🔴 SWM-ACCT-WS11

**Status:** Confirmed malicious execution

- Malicious Office document opened
- Macro enabled
- PowerShell executed
- External connection to known infrastructure
- Endpoint isolated

### 🔴 SWM-OPS-WS19

**Status:** Confirmed compromised

- Malicious Office document opened
- Macro enabled
- PowerShell executed
- C2 communication
- `update.dll` executed
- 12 documents accessed
- Additional outbound connection observed
- Associated account temporarily disabled
- Endpoint isolated

### 🟡 SWM-HR-WS07

**Status:** Exposed — no evidence of compromise

- Malicious document downloaded
- Document opened
- Macro was not enabled
- No malicious child processes
- No PowerShell
- No C2 communication
- No persistence
- No credential-access activity
- No lateral movement observed

---

## Investigation Process

The investigation followed an evidence-based incident-response process:

1. EDR alert triage
2. Process-tree analysis
3. PowerShell investigation
4. Network and DNS analysis
5. Threat hunting across endpoints
6. Email campaign investigation
7. Authentication review
8. Persistence investigation
9. Credential-access investigation
10. Lateral-movement investigation
11. Data-exfiltration investigation
12. Evidence preservation
13. Containment
14. Eradication planning
15. Recovery validation

---

## MITRE ATT&CK Mapping

| Technique | Description | Evidence |
|---|---|---|
| **T1204.002** | User Execution: Malicious File | User opened malicious Office document and enabled the macro |
| **T1059.001** | Command and Scripting Interpreter: PowerShell | Malicious PowerShell execution |
| **T1027** | Obfuscated/Compressed Files and Information | Encoded PowerShell command |
| **T1218.011** | System Binary Proxy Execution: Rundll32 | `rundll32.exe` executed `update.dll` |
| **T1071.001** | Application Layer Protocol: Web Protocols | C2 communication over HTTPS |
| **T1003.001** | OS Credential Dumping: LSASS Memory | LSASS access attempt observed; access denied |

---

## Data Exfiltration Assessment

Potential data exfiltration was investigated on `SWM-OPS-WS19`.

The endpoint showed:

**Malicious DLL → sensitive files accessed → subsequent outbound HTTPS connection**

However, available telemetry did **not** establish that the contents of those files were transmitted.

### Assessment

**Potential data exfiltration — not confirmed**

This distinction was maintained throughout the investigation because file access alone does not prove data theft.

---

## Containment

Containment actions included:

- Isolation of confirmed compromised endpoints
- Quarantine of malicious email
- Identification of malicious IP/domain/URL
- Identification of malicious file hashes
- Temporary disabling of the affected OPS-WS19 account
- Preservation of forensic evidence
- Continued threat hunting for additional affected systems

---

## Eradication & Recovery

The planned remediation process included:

- Terminate/quarantine malicious processes
- Quarantine malicious files
- Remove confirmed malicious payloads
- Check persistence mechanisms
- Run comprehensive EDR/AV scans
- Re-scan for known indicators
- Review credential exposure
- Validate system integrity
- Obtain incident-response approval before reconnection
- Increase monitoring after recovery

---

## Analyst Lessons Learned

### Evidence vs. Assumption

I practiced separating:

**What I know → What I suspect → What I need to prove**

### Important Lessons

- Exposure does not automatically mean compromise.
- Suspicious outbound traffic does not automatically prove exfiltration.
- File access does not automatically prove data theft.
- Execution-policy bypass is not privilege escalation by itself.
- MITRE ATT&CK provides a framework for describing and investigating attacker behavior.
- Known malicious indicators can be blocked while suspicious behaviors may require alerting and investigation.
- Evidence should be preserved before eradication when forensic investigation is still required.

---

## Incident Response Lifecycle

**Detection → Investigation → Threat Hunting → Scope → Containment → Evidence Preservation → Eradication → Recovery**

---

## Skills Practiced

**Security Operations (SOC)**  
**EDR Investigation**  
**Threat Hunting**  
**Phishing Analysis**  
**Network Investigation**  
**DNS Analysis**  
**MITRE ATT&CK**  
**Incident Response**  
**Evidence Preservation**  
**Containment & Eradication**  
**Recovery Planning**  
**Technical Documentation**

---

## Portfolio Note

This project is part of a structured cybersecurity career simulation designed to practice realistic junior SOC analyst responsibilities.

**This is simulated work and is not real employment or a real security incident.**
