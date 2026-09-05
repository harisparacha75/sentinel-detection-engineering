# Suspicious PowerShell Detection

## Overview

This detection identifies PowerShell activity containing command-line
patterns commonly associated with malicious execution, command obfuscation,
or remote content retrieval.

PowerShell is widely used by administrators and legitimate applications,
so the detection should be tuned using organizational baselines and
additional endpoint context.

## Detection Objective

Identify potentially suspicious PowerShell execution involving:

- Encoded commands
- Base64 decoding
- Dynamic command execution
- Remote content retrieval
- Suspicious download mechanisms

## MITRE ATT&CK

- **T1059.001** — PowerShell

## Platform

Microsoft Sentinel

## Data Source

Microsoft Defender for Endpoint

Primary table:

`DeviceProcessEvents`

## Detection Logic

The detection:

1. Reviews recent endpoint process activity.
2. Identifies PowerShell processes.
3. Examines the PowerShell command line.
4. Searches for suspicious execution or download patterns.
5. Returns process and parent-process context for investigation.

## Suspicious Patterns

Examples include:

| Pattern | Potential Behavior |
|---|---|
| `-EncodedCommand` | Command obfuscation |
| `FromBase64String` | Base64 decoding |
| `Invoke-Expression` / `IEX` | Dynamic code execution |
| `DownloadString` | Remote content retrieval |
| `Invoke-WebRequest` | Web-based content retrieval |
| `Start-BitsTransfer` | File transfer |

These indicators are not inherently malicious and should be evaluated
alongside process, user, parent-process, and network context.

## Investigation Steps

When the detection triggers:

1. Identify the affected device.
2. Identify the user executing PowerShell.
3. Review the complete PowerShell command line.
4. Examine the parent process.
5. Determine how PowerShell was launched.
6. Check for encoded or obfuscated content.
7. Review network connections from the process.
8. Identify downloaded or created files.
9. Search for related PowerShell activity on other endpoints.
10. Determine whether the activity is administrative or malicious.

## Important Process Relationships

Particular attention should be given to suspicious parent-child relationships,
such as:

```text
Microsoft Office
      ↓
PowerShell
      ↓
Network connection
