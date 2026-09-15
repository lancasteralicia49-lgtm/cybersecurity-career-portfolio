# SIMULATION — Incident 001 Indicators of Compromise

> This document contains fictional indicators from a cybersecurity career simulation.

## Network Indicators

| Type | Indicator | Significance |
|---|---|---|
| Malicious IP | `185.XX.XX.47` | External infrastructure associated with payload download and C2 communication |
| Malicious Domain | `invoice-update[.]com` | Domain associated with phishing campaign and C2 activity |
| Malicious URL | `https://invoice-update[.]com/update` | URL used to retrieve remote content |

## File Indicators

| Type | Indicator | Significance |
|---|---|---|
| Malicious Document | `Invoice_September_2026.docm` | Phishing attachment |
| Document SHA-256 | `7f3c...91a2` | Identifies the malicious document |
| Malicious DLL | `update.dll` | Payload executed through `rundll32.exe` |
| DLL SHA-256 | `91ab...72ef` | Identifies the malicious DLL |

## Behavioral Indicators

### PowerShell

Observed behaviors included:

- `-ExecutionPolicy Bypass`
- `-WindowStyle Hidden`
- `-EncodedCommand`
- Remote content download
- `IEX` / `Invoke-Expression`

### Process Chain

Observed execution chain:

`explorer.exe → WINWORD.EXE → powershell.exe → rundll32.exe`

### Credential Access Attempt

PowerShell attempted to access:

`lsass.exe`

The attempt was **denied**.

## Threat-Hunting Searches

The indicators were searched across the environment to identify additional affected systems.

Search targets included:

- Document filename
- Document SHA-256
- DLL filename
- DLL SHA-256
- Malicious IP
- Malicious domain
- Malicious URL
- Office-to-PowerShell execution
- Encoded PowerShell
- Suspicious `rundll32.exe` execution
- Suspicious LSASS access

## Known Scope

- `Invoice_September_2026.docm`: 3 endpoints
- Document hash: 3 endpoints
- `invoice-update[.]com`: 4 endpoints
- `185.XX.XX.47`: 4 endpoints
- `update.dll` hash: 1 confirmed endpoint + 2 suspicious events

## Recommended Security Actions

- Block known malicious IP and domain.
- Block/quarantine known malicious URL.
- Detect/quarantine matching document and DLL hashes.
- Alert on suspicious Office-to-PowerShell behavior.
- Alert on encoded PowerShell commands.
- Detect suspicious `rundll32.exe` execution.
- Continue monitoring for recurrence of known indicators.

## Analyst Note

Known indicators are useful for immediate containment and threat hunting. Behavioral indicators are also important because attackers can change filenames, domains, IP addresses, or hashes while keeping similar execution techniques.
