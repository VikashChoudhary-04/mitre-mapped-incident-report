# Incident Investigation Report

## Incident Title

- Suspicious Windows Authentication and Process Activity Investigation

---

## Executive Summary

- A security investigation was conducted using Windows Security Event Logs within Splunk to identify suspicious authentication behavior, privileged activity, and potential attacker-related process execution.

- The investigation focused on authentication telemetry, privileged logons, process creation activity, and suspicious command execution patterns.

- No confirmed malicious compromise or active attacker behavior was identified in the reviewed baseline dataset. However, the investigation demonstrates a structured SOC investigation workflow using MITRE ATT&CK mapping and threat hunting methodology.

---

## Investigation Scope

| Category | Details |
|---|---|
| SIEM Platform | Splunk Free |
| Log Source | Windows Security Logs |
| Investigation Type | Host-Based Security Investigation |
| Analysis Focus | Authentication and Process Activity |
| Host | Vikash |

---

## Event IDs Investigated

| Event ID | Description |
|---|---|
| 4624 | Successful Logon |
| 4625 | Failed Logon |
| 4672 | Privileged Logon |
| 4688 | Process Creation |

---

## Investigation Methodology

- The investigation included:

  1. Authentication monitoring
  2. Failed login analysis
  3. Privileged account review
  4. Process execution hunting
  5. Suspicious command analysis
  6. ATT&CK technique mapping
  7. Timeline creation
  8. Analyst assessment

---

## Investigation Findings

---

### 1. Successful Logon Analysis

#### SPL Query

```spl
index=main "4624"
| stats count by host
| sort - count
```

#### Purpose

- Review successful authentication activity across the environment.

#### Findings

- Multiple successful authentication events were identified and reviewed.

- Observed authentication activity appeared consistent with expected baseline Windows behavior.

- No suspicious login anomalies or evidence of unauthorized authentication were identified.

---

### 2. Failed Login Analysis

#### SPL Query

```spl id="5u3b8x"
index=main "4625"
| stats count by host
| sort - count
```

#### Purpose

- Identify failed authentication attempts and potential brute force activity.

#### Findings

- No failed authentication events were identified within the current dataset.

- No evidence of brute force or credential abuse activity was observed.

---

### 3. Privileged Logon Monitoring

#### SPL Query

```spl id="r8k2vw"
index=main "4672"
| stats count by host
| sort - count
```

#### Purpose

- Monitor elevated authentication activity and privileged account usage.

#### Findings

- Privileged logon activity was reviewed and appeared consistent with normal Windows system startup and administrative behavior.

- No suspicious privileged escalation activity was identified.

---

### 4. Process Creation Investigation

#### SPL Query

```spl id="v4n7ta"
index=main "4688"
| stats count by host
| sort - count
```

#### Purpose

- Investigate process execution telemetry and identify suspicious activity.

#### Findings

- Process creation events were reviewed for:

  * suspicious binaries
  * PowerShell activity
  * LOLBin execution
  * anomalous command execution

- Observed process activity primarily reflected standard Windows system initialization processes.

---

### 5. Suspicious Process Hunting

#### SPL Query

```spl id="b7y4mz"
index=main ("powershell" OR "cmd.exe" OR "rundll32" OR "mshta")
```

#### Purpose

- Hunt for suspicious command execution associated with attacker behavior.

#### Findings

- No suspicious PowerShell execution, LOLBin abuse, or malicious command execution was identified in the reviewed dataset.

---

## MITRE ATT&CK Mapping

| Investigation Activity       | ATT&CK Technique              | Technique ID |
| ---------------------------- | ----------------------------- | ------------ |
| Failed Login Monitoring      | Brute Force                   | T1110        |
| Successful Logon Correlation | Valid Accounts                | T1078        |
| PowerShell Hunting           | PowerShell                    | T1059.001    |
| LOLBin Monitoring            | Signed Binary Proxy Execution | T1218        |

---

## Incident Timeline

| Approximate Activity  | Description                                             |
| --------------------- | ------------------------------------------------------- |
| Authentication Events | Successful Windows logons observed                      |
| Privileged Activity   | SYSTEM and privileged logons identified                 |
| Process Creation      | Standard Windows initialization processes executed      |
| Threat Hunting        | No suspicious PowerShell or LOLBin execution identified |

---

## Analyst Assessment

- The reviewed dataset primarily reflected baseline Windows operating system activity and standard authentication behavior.

- No confirmed indicators of compromise, malicious persistence, privilege escalation, or attacker command execution were identified during the investigation.

- The investigation successfully demonstrated:

  * Splunk-based SOC investigation workflows
  * ATT&CK-based analysis
  * Windows event analysis
  * Detection engineering concepts
  * Threat hunting methodology

---

## Recommendations

- Recommended future improvements include:

  * Enable Sysmon telemetry
  * Improve field extraction and parsing
  * Integrate threat intelligence
  * Build automated detections
  * Expand authentication telemetry
  * Implement endpoint monitoring

---

## Lessons Learned

- Key investigation lessons included:

  * Baseline analysis is critical for SOC investigations
  * Threat hunting requires contextual understanding
  * ATT&CK mapping improves analytical consistency
  * Windows Event IDs provide valuable telemetry
  * Detection engineering combines logic and investigation
  * SOC reporting requires structured analytical thinking

---

## Final Conclusion

- No confirmed malicious activity was identified within the reviewed baseline dataset.

- This investigation successfully demonstrated a structured SOC investigation and MITRE ATT&CK mapping workflow using Splunk, Windows Security Logs, and threat hunting methodologies.
