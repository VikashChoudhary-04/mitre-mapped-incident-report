# Investigation Timeline

- This timeline documents the sequence of events and investigative observations identified during the SOC investigation.

---

## Timeline Overview

- The investigation focused on:
  - authentication activity
  - privileged logons
  - process creation telemetry
  - suspicious command execution
  - threat hunting findings

- The timeline below summarizes the investigative workflow and observed activity.

---

## Timeline Events

| Approximate Activity | Description | Relevant Event ID | Investigation Notes |
|---|---|---|---|
| Windows System Startup | Core Windows processes initialized | 4688 | Standard Windows startup activity observed |
| Successful Authentication Events | Multiple successful logons identified | 4624 | Authentication activity appeared consistent with normal baseline behavior |
| Privileged Logon Activity | SYSTEM and elevated logons observed | 4672 | Privileged activity appeared associated with standard system operations |
| Process Creation Events | Windows initialization processes executed | 4688 | No suspicious process execution identified |
| Threat Hunting Activity | PowerShell and LOLBin review performed | 4688 | No malicious command execution identified |
| Authentication Review | Failed authentication telemetry reviewed | 4625 | No failed login activity identified in dataset |

---

## Investigation Sequence

### Phase 1 — Authentication Analysis

- The investigation began with reviewing authentication telemetry to identify:
  - successful logons
  - failed logons
  - suspicious authentication patterns
  - brute force indicators

- Primary Event IDs:
  - 4624
  - 4625

---

### Phase 2 — Privileged Activity Review

- Privileged authentication activity was reviewed to identify:
  - elevated sessions
  - administrative activity
  - privilege escalation indicators

- Primary Event ID:
  - 4672

---

### Phase 3 — Process Execution Investigation

- Process creation telemetry was analyzed for:
  - suspicious binaries
  - PowerShell execution
  - LOLBin usage
  - anomalous command execution

- Primary Event ID:
  - 4688

---

### Phase 4 — Threat Hunting

- Threat hunting activities focused on:
  - PowerShell abuse
  - cmd.exe activity
  - rundll32.exe usage
  - mshta.exe execution

- No suspicious command execution was identified.

---

## ATT&CK Mapping Timeline

| Timeline Activity | ATT&CK Technique |
|---|---|
| Failed Login Review | T1110 - Brute Force |
| Successful Logon Analysis | T1078 - Valid Accounts |
| PowerShell Hunting | T1059.001 - PowerShell |
| LOLBin Monitoring | T1218 - Signed Binary Proxy Execution |

---

## Timeline Assessment

- The reviewed telemetry primarily reflected:
  - baseline Windows activity
  - standard authentication behavior
  - normal system initialization
  - expected privileged operations

- No confirmed indicators of:
  - compromise
  - malicious persistence
  - privilege escalation
  - attacker execution
were identified during the investigation.

---

## Key Lessons Learned

- Timeline analysis improves SOC investigations
- Event sequencing helps contextualize activity
- Authentication telemetry is critical for investigations
- Threat hunting improves analytical visibility
- ATT&CK mapping strengthens investigation consistency

---

## Project Context

- This timeline was created as part of a beginner SOC investigation and MITRE ATT&CK mapping project using:
  - Splunk
  - Windows Security Logs
  - Threat hunting methodology
  - Incident reporting workflows
