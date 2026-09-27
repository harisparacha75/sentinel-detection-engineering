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
| Password Spray | T1110.003 | Implemented |
| Brute Force Authentication | T1110 | Implemented |
| Suspicious PowerShell | T1059.001 | Implemented |
| Impossible Travel | T1078 |Implemented |
| Privilege Escalation | T1548 | Implemented |
| Suspicious Account Activity | T1078 | Implemented |

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

---

## 🚀 Deployment Guide

This section explains how to deploy the detection rules in Microsoft Sentinel.

### Prerequisites

Before deploying the detections, ensure you have:

- An active Microsoft Azure subscription.
- A Microsoft Sentinel-enabled Log Analytics workspace.
- Appropriate permissions to create and manage analytics rules.
- The required data connectors configured to ingest authentication and endpoint telemetry.

### Data Sources

| Detection | Required Data Source |
|---|---|
| Password Spray | SigninLogs |
| Brute Force Authentication | SigninLogs |
| Impossible Travel | SigninLogs |
| Suspicious PowerShell | DeviceProcessEvents |

### Deployment Steps

1. Open the Microsoft Sentinel workspace in the Azure portal.
2. Navigate to the Logs section.
3. Copy the relevant KQL query from the `detections/` directory.
4. Run the query and review the returned events.
5. Navigate to Analytics and create a scheduled analytics rule.
6. Configure the rule name, severity, query scheduling, and alert settings.
7. Set the required entity mappings and incident settings.
8. Save the rule and enable it.

### Customization

Detection thresholds and time windows should be adjusted according to the organization's environment, authentication patterns, and security requirements.

### Important Note

These detection rules are provided for learning and portfolio purposes. Review and adapt each query before deploying it in a production environment.
tuning/
screenshots/
