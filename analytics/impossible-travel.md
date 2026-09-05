# Impossible Travel Detection

## Overview

This detection identifies potentially suspicious successful authentication
activity where the same user appears to authenticate from geographically
distant locations within a time period that would require an unrealistic
travel speed.

This can indicate possible account compromise or the use of stolen
credentials.

## Detection Objective

Identify successful authentication events where the distance between
consecutive login locations and the time between those events results in
an unusually high required travel speed.

## MITRE ATT&CK

- **T1078** — Valid Accounts

## Platform

Microsoft Sentinel

## Data Source

Microsoft Entra ID / Azure AD Sign-in Logs

Primary table:

`SigninLogs`

## Detection Logic

The detection:

1. Reviews successful authentication events.
2. Extracts geographic information from sign-in events.
3. Groups events by user.
4. Compares consecutive authentication locations.
5. Calculates the geographic distance between locations.
6. Calculates the time between authentication events.
7. Calculates the required travel speed.
8. Flags activity where the required speed exceeds the defined threshold.

### Current threshold

| Parameter | Value |
|---|---:|
| Lookback window | 24 hours |
| Travel speed threshold | > 800 km/h |

The threshold is an example and should be tuned based on the organization's
environment and authentication patterns.

## Example Attack Scenario

```text
User
 │
 ├── 09:00 → Islamabad
 │
 └── 10:00 → London
              │
              └── Travel time is unrealistic
