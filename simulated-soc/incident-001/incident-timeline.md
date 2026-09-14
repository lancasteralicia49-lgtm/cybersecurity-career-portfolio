# SIMULATION — Incident 001 Timeline

**Date:** September 14, 2026

> This timeline documents a fictional cybersecurity incident used for skills development.

---

## Timeline

### 08:12
Phishing email received by 11 employees.

**Subject:** September Invoice — Action Required

The email contained:
- Malicious `.docm` attachment
- Malicious URL

### 08:37
`SWM-HR-WS07` downloaded `Invoice_September_2026.docm` through Chrome.

### 08:38
`SWM-HR-WS07` opened the document.

The macro was **not enabled** and no malicious execution or C2 activity was observed.

### 08:41:48
`j.morrison` visited `invoice-update[.]com`.

### 08:42:06
`SWM-FIN-WS23` opened `Invoice_September_2026.docm`.

The user enabled the macro.

### 08:42:19
PowerShell connected to:

`185.XX.XX.47:443`

The connection was used to download the malicious payload.

### 08:42–08:43
`update.dll` was executed through `rundll32.exe`.

PowerShell also attempted to access `lsass.exe`, but access was denied.

### 08:51:44
`SWM-ACCT-WS11` demonstrated similar malicious PowerShell and external C2 activity.

### 09:03:17
`SWM-OPS-WS19` contacted `185.XX.XX.47:443` through PowerShell and downloaded the payload.

### 09:03:41
`update.dll` accessed 12 documents on `SWM-OPS-WS19`.

Examples included:

- `Production_Schedule.xlsx`
- `Supplier_List.xlsx`
- `Project_Status.docx`

Several contained sensitive business information.

### 09:04:27
`update.dll` made another HTTPS connection to `185.XX.XX.47`.

**Outbound:** 14.6 KB  
**Inbound:** 1.2 KB

Potential data exfiltration was identified but **not confirmed**.

---

## Containment

- `SWM-FIN-WS23` isolated
- `SWM-ACCT-WS11` isolated
- `SWM-OPS-WS19` isolated
- `SWM-HR-WS07` classified as exposed, not compromised
- Malicious emails quarantined
- Known malicious indicators identified
- OPS-WS19 associated account temporarily disabled
- Forensic evidence preserved

---

## Current Assessment

**Incident Severity:** HIGH

**Confirmed compromised:** 3 endpoints

**Exposed:** 1 endpoint

**Targeted employees:** 11

**Potential data exfiltration:** Not confirmed

**Current response phase:** Eradication / Recovery
