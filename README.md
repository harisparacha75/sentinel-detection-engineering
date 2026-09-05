# Microsoft Sentinel Detection Engineering Lab

A practical security engineering lab focused on detection engineering,
threat hunting, incident investigation, and security monitoring using
Microsoft Sentinel and KQL.

> This project is developed in a simulated lab environment for
> educational and portfolio purposes.

---

## 🎯 Objectives

- Develop practical Microsoft Sentinel detection rules
- Write and optimize KQL queries
- Investigate suspicious security events
- Map detections to MITRE ATT&CK
- Identify and reduce false positives
- Develop threat-hunting queries
- Document incident investigation workflows
- Apply detection engineering principles to realistic attack scenarios

---

## 🛠️ Technologies

- Microsoft Sentinel
- Kusto Query Language (KQL)
- Microsoft Defender
- Microsoft Entra ID
- Windows Security Events
- MITRE ATT&CK
- Sigma

---

## 🔎 Detection Use Cases

| Detection | MITRE ATT&CK | Status |
|---|---|---|
| Password Spray | T1110.003 | Planned |
| Brute Force Authentication | T1110 | Planned |
| Suspicious PowerShell | T1059.001 | Planned |
| Impossible Travel | T1078 | Planned |
| Privilege Escalation | T1548 | Planned |
| Suspicious Account Activity | T1078 | Planned |

---

## 🔬 Detection Engineering Process

Each detection follows this workflow:

Threat Behavior  
↓  
Telemetry  
↓  
Detection Hypothesis  
↓  
KQL Query  
↓  
Alert Generation  
↓  
Investigation  
↓  
MITRE ATT&CK Mapping  
↓  
False Positive Analysis  
↓  
Detection Tuning

---

## 📂 Repository Structure

```text
detections/
├── authentication/
├── execution/
├── privilege-escalation/
├── persistence/
└── defense-evasion/

hunting/
├── authentication/
├── endpoint/
└── identity/

investigations/
├── incident-001/
├── incident-002/
└── incident-003/

mitre/
tuning/
screenshots/
