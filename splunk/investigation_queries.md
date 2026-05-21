# Investigation Queries (Splunk SPL)

- This document contains Splunk SPL queries used during the SOC investigation and ATT&CK-mapped incident analysis.

---

## 1. Successful Authentication Analysis

```spl
index=main "4624"
| stats count by host
| sort - count
````

### Purpose

- Review successful Windows authentication activity.

### Investigation Goal

- Identify:

  * suspicious authentication patterns
  * abnormal logon behavior
  * potential unauthorized access

---

## 2. Failed Authentication Monitoring

```spl id="z7v2mk"
index=main "4625"
| stats count by host
| sort - count
```

### Purpose

- Review failed authentication attempts.

### Investigation Goal

- Detect:

  * brute force activity
  * password spraying
  * repeated login failures

---

## 3. Privileged Logon Monitoring

```spl id="g4p8yx"
index=main "4672"
| stats count by host
| sort - count
```

### Purpose

- Monitor elevated authentication activity.

### Investigation Goal

- Identify:

  * privileged account usage
  * suspicious administrative access
  * elevated sessions

---

## 4. Process Creation Investigation

```spl id="t9k3bv"
index=main "4688"
| stats count by host
| sort - count
```

### Purpose

- Review Windows process execution activity.

### Investigation Goal

- Identify:

  * suspicious binaries
  * anomalous process behavior
  * execution telemetry

---

## 5. Suspicious PowerShell Hunting

```spl id="f8r2zn"
index=main ("powershell" OR "cmd.exe" OR "rundll32" OR "mshta")
```

### Purpose

- Hunt for suspicious command execution activity.

### Investigation Goal

- Detect:

  * PowerShell abuse
  * LOLBin execution
  * malicious scripting activity
  * defense evasion behavior

---

## 6. Authentication Timeline Analysis

```spl id="u5x1qa"
index=main "4624"
| timechart count
```

### Purpose

- Visualize authentication activity over time.

### Investigation Goal

- Identify:

  * authentication spikes
  * unusual activity bursts
  * anomalous login timing

---

## 7. Process Activity Timeline

```spl id="n7b4rw"
index=main "4688"
| timechart count
```

### Purpose

- Visualize process execution activity over time.

### Investigation Goal

- Identify:

  * execution spikes
  * unusual process activity
  * anomalous system behavior

---

## Event IDs Investigated

| Event ID | Description      |
| -------- | ---------------- |
| 4624     | Successful Logon |
| 4625     | Failed Logon     |
| 4672     | Privileged Logon |
| 4688     | Process Creation |

---

## MITRE ATT&CK Mapping

| Query Purpose                      | ATT&CK Technique                          |
| ---------------------------------- | ----------------------------------------- |
| Failed Authentication Monitoring   | T1110 - Brute Force                       |
| Successful Authentication Analysis | T1078 - Valid Accounts                    |
| PowerShell Hunting                 | T1059.001 - PowerShell                    |
| LOLBin Monitoring                  | T1218 - Signed Binary Proxy Execution     |
| Process Creation Analysis          | T1059 - Command and Scripting Interpreter |

---

## Detection Engineering Concepts

- This investigation demonstrates:

  * Threat hunting methodology
  * Authentication monitoring
  * Process execution analysis
  * ATT&CK-based investigation
  * Detection engineering fundamentals
  * SOC analytical workflows

---

## Analyst Notes

- These queries were developed as part of a beginner SOC investigation and MITRE ATT&CK mapping project using:

  * Splunk
  * Windows Security Event Logs
  * Threat hunting methodology
  * ATT&CK analysis
  * Incident response workflows
