# MITRE ATT&CK Mapping

- This file documents the MITRE ATT&CK techniques associated with the investigation findings and threat hunting activities performed during this SOC incident investigation project.

---

## ATT&CK Overview

- MITRE ATT&CK is a framework used to:
  - classify attacker behavior
  - standardize investigations
  - improve detection engineering
  - map security telemetry to adversary techniques

- This investigation used ATT&CK mapping to improve:
  - analytical consistency
  - detection logic
  - SOC reporting quality
  - threat hunting context

---

## Investigation Mapping

| Investigation Activity | ATT&CK Technique | Technique ID | Tactic |
|---|---|---|---|
| Failed Login Monitoring | Brute Force | T1110 | Credential Access |
| Successful Authentication Analysis | Valid Accounts | T1078 | Defense Evasion |
| PowerShell Hunting | PowerShell | T1059.001 | Execution |
| LOLBin Monitoring | Signed Binary Proxy Execution | T1218 | Defense Evasion |
| Process Creation Investigation | Command and Scripting Interpreter | T1059 | Execution |

---

## Technique Details

---

### T1110 — Brute Force

#### Description

- Attackers attempt repeated authentication attempts to gain unauthorized access.

#### Investigation Relevance

- Failed authentication monitoring helps identify:
  - brute force attacks
  - password spraying
  - credential abuse
  - account targeting

#### Relevant Telemetry

- Windows Event ID 4625
- Authentication logs
- Login telemetry

#### Findings

- No failed authentication spikes or brute force indicators were identified in the reviewed dataset.

---

### T1078 — Valid Accounts

#### Description

- Attackers abuse legitimate credentials to evade detection and maintain access.

#### Investigation Relevance

- Successful authentication activity may indicate:
  - unauthorized account usage
  - credential compromise
  - suspicious logon patterns

#### Relevant Telemetry

- Windows Event ID 4624
- Privileged authentication activity
- Account usage patterns

#### Findings

- Observed successful authentication activity appeared consistent with expected Windows baseline behavior.

---

### T1059.001 — PowerShell

#### Description

- Attackers commonly abuse PowerShell for:
  - malware execution
  - automation
  - persistence
  - lateral movement

#### Investigation Relevance

- Monitoring PowerShell activity helps identify:
  - suspicious scripting
  - post-exploitation behavior
  - malicious command execution

#### Relevant Indicators

- powershell.exe
- encoded commands
- suspicious execution chains

#### Findings

- No suspicious PowerShell activity was identified during threat hunting.

---

### T1218 — Signed Binary Proxy Execution

#### Description

- Attackers abuse legitimate Windows binaries (LOLBins) to evade detection.

#### Common LOLBins

- rundll32.exe
- mshta.exe
- regsvr32.exe
- certutil.exe

#### Investigation Relevance

- LOLBin monitoring improves visibility into:
  - defense evasion
  - malicious execution
  - proxy execution techniques

#### Findings

- No suspicious LOLBin abuse was identified in the reviewed telemetry.

---

### T1059 — Command and Scripting Interpreter

#### Description

- Attackers use command interpreters and scripting engines to execute malicious actions.

#### Investigation Relevance

- Process creation monitoring helps identify:
  - suspicious commands
  - malware execution
  - anomalous process behavior

#### Relevant Telemetry

- Windows Event ID 4688
- Process execution events
- Command-line activity

#### Findings

- Reviewed process creation activity primarily reflected normal Windows initialization and system behavior.

---

## ATT&CK Value For SOC Analysts

- MITRE ATT&CK helps analysts:
  - understand attacker behavior
  - improve investigations
  - standardize detections
  - build stronger reports
  - prioritize suspicious activity

---

## Key Lessons Learned

- ATT&CK mapping improves investigation consistency
- Authentication telemetry is critical for SOC visibility
- Threat hunting requires contextual analysis
- Detection engineering combines telemetry and attacker behavior understanding
- Baseline system knowledge is essential for identifying anomalies

---

## Project Context

- This ATT&CK mapping was created as part of a beginner SOC investigation and threat hunting project using:
  - Splunk
  - Windows Security Logs
  - Threat hunting methodology
  - Detection engineering concepts
  - MITRE ATT&CK mapping
