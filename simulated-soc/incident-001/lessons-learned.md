# SIMULATION — Incident 001 Lessons Learned

> This document summarizes lessons from a fictional SOC incident-response exercise.

## Investigation Lessons

### 1. Start with the evidence

I learned to separate:

**What I know → What I suspect → What I need to prove**

This prevented unsupported conclusions during the investigation.

### 2. Exposure is not the same as compromise

`SWM-HR-WS07` downloaded and opened the malicious document, but the macro was not enabled and no malicious execution or C2 activity was observed.

The endpoint was therefore classified as:

**Exposed — no evidence of compromise**

### 3. Outbound traffic is not automatically exfiltration

The compromised OPS endpoint accessed sensitive documents and later communicated with the external C2 infrastructure.

This created a strong suspicion of possible data exfiltration, but the available evidence did not prove that the documents were transmitted.

### 4. Execution-policy bypass is not privilege escalation

The PowerShell command used:

`-ExecutionPolicy Bypass`

This bypasses PowerShell execution-policy restrictions but does not by itself provide elevated privileges.

### 5. Threat hunting expands incident scope

The investigation started from a single EDR alert but expanded after searching for:

- Document filename
- File hashes
- Domain
- IP address
- DLL
- PowerShell behavior
- Related network activity

This identified additional affected systems and revealed a broader phishing campaign.

### 6. MITRE ATT&CK supports investigation

MITRE ATT&CK provided a standardized way to describe observed attacker behavior.

I learned that I do not need to memorize every technique ID. The important skill is recognizing the behavior, collecting evidence, and then mapping the evidence to the appropriate technique.

### 7. Preserve evidence before eradication

Forensic evidence should be preserved before deleting malicious files or rebuilding systems when further investigation is required.

This helps determine:

- What happened
- How the attacker operated
- What systems were affected
- Whether credentials or data may have been exposed

### 8. Containment should be targeted

Known malicious infrastructure and artifacts can be blocked or quarantined immediately.

Suspicious legitimate tools such as PowerShell or `rundll32.exe` should generally be handled through appropriate detection and security controls rather than blindly blocking the tools themselves.

---

## Incident Response Lifecycle Practiced

**Detection → Investigation → Threat Hunting → Scope → Containment → Evidence Preservation → Eradication → Recovery**

---

## Skills Developed

- SOC alert triage
- EDR investigation
- Threat hunting
- Phishing analysis
- Network analysis
- DNS investigation
- Process-tree analysis
- MITRE ATT&CK mapping
- Evidence preservation
- Incident containment
- Eradication planning
- Recovery validation
- Technical documentation
- Evidence-based decision making

---

## Reflection

This exercise helped me understand how a cybersecurity analyst moves from an individual alert to a broader incident investigation.

The biggest lesson was that good incident response is not about making the fastest assumption. It is about collecting the right evidence, determining what the evidence actually proves, and communicating uncertainty when something has not yet been confirmed.

---

## Portfolio Note

This is part of a structured cybersecurity career simulation designed to develop practical SOC and incident-response skills.

**This is simulated work and is not real employment or a real security incident.**
