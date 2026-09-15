# SIMULATION — Incident 001 MITRE ATT&CK Mapping

> This document maps observed behavior from a fictional cybersecurity incident to MITRE ATT&CK techniques. Technique IDs were researched during the investigation and were not assumed to indicate activity without supporting evidence.

## Technique Summary

| ATT&CK ID | Technique | What It Means | Evidence Observed | Assessment |
|---|---|---|---|---|
| **T1204.002** | User Execution: Malicious File | A user is tricked into opening a malicious file. | Employees opened `Invoice_September_2026.docm`; several enabled the macro. | Confirmed |
| **T1059.001** | Command and Scripting Interpreter: PowerShell | PowerShell is used to execute commands or scripts. | Malicious Office content launched PowerShell. | Confirmed |
| **T1027** | Obfuscated/Compressed Files and Information | Information or commands are obscured to make analysis harder. | PowerShell used an encoded command. | Confirmed |
| **T1218.011** | System Binary Proxy Execution: Rundll32 | `rundll32.exe` is abused to execute a DLL. | `rundll32.exe` executed `update.dll`. | Confirmed |
| **T1071.001** | Application Layer Protocol: Web Protocols | Attackers use normal web protocols for communication. | Malicious processes communicated with external infrastructure over HTTPS. | Confirmed |
| **T1003.001** | OS Credential Dumping: LSASS Memory | Attackers attempt to obtain credentials from LSASS memory. | PowerShell attempted to access `lsass.exe`; access was denied. | Attempt observed |

---

## 1. T1204.002 — User Execution: Malicious File

### What it means

The attacker relies on a user to open a malicious file.

### Evidence

The phishing campaign delivered:

`Invoice_September_2026.docm`

Multiple employees opened the document. On compromised endpoints, users enabled the macro.

### Assessment

**Confirmed.**

---

## 2. T1059.001 — Command and Scripting Interpreter: PowerShell

### What it means

PowerShell is used to execute commands or scripts.

### Evidence

The malicious Office document launched PowerShell.

Observed command-line behavior included:

- `-ExecutionPolicy Bypass`
- `-WindowStyle Hidden`
- `-EncodedCommand`

The decoded script downloaded remote content and executed it.

### Assessment

**Confirmed.**

---

## 3. T1027 — Obfuscated/Compressed Files and Information

### What it means

Attackers may obscure commands or information to make analysis more difficult.

### Evidence

The PowerShell command contained an encoded command.

### Assessment

**Confirmed.**

---

## 4. T1218.011 — System Binary Proxy Execution: Rundll32

### What it means

Attackers can abuse a legitimate Windows utility to execute malicious DLL code.

### Evidence

The malicious payload:

`update.dll`

was executed using:

`rundll32.exe`

### Assessment

**Confirmed.**

---

## 5. T1071.001 — Application Layer Protocol: Web Protocols

### What it means

Attackers may use normal web protocols such as HTTP/HTTPS for command-and-control communication.

### Evidence

Compromised endpoints communicated with:

`185.XX.XX.47:443`

The malicious infrastructure was associated with:

`invoice-update[.]com`

The communication occurred over HTTPS.

### Assessment

**Confirmed.**

---

## 6. T1003.001 — OS Credential Dumping: LSASS Memory

### What it means

An attacker attempts to access LSASS memory to obtain credentials or credential material.

### Evidence

At approximately 08:43, PowerShell attempted to access:

`lsass.exe`

The attempt was **denied**.

### Assessment

**Attempt observed — successful credential dumping was not confirmed.**

This distinction is important because an attempted technique does not prove successful credential compromise.

---

# Techniques Investigated but Not Confirmed

The investigation also checked for several additional behaviors:

- Persistence through scheduled tasks
- Persistence through services
- Registry Run/RunOnce persistence
- Startup persistence
- Privilege escalation
- Credential theft
- Lateral movement
- RDP
- WinRM
- PsExec
- Suspicious SMB activity

No confirmed evidence of these activities was identified during the investigation.

---

# Analyst Methodology

MITRE ATT&CK was used as an **investigative framework**, not as a replacement for evidence.

The investigation followed:

**Observed Behavior → Evidence Collection → ATT&CK Mapping → Assessment**

This helped distinguish between:

- Confirmed activity
- Attempted activity
- Suspected activity
- Activity that was investigated but not observed

---

# Key Lesson

I learned that I do not need to memorize MITRE ATT&CK technique IDs.

The important analyst skill is recognizing the behavior, collecting evidence, and then using ATT&CK to describe that behavior consistently.
