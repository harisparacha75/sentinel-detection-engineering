# Password Spray Detection

## Overview

This detection identifies potential password spraying activity against
multiple user accounts from a common source IP address.

Password spraying differs from traditional brute-force attacks because
the attacker typically attempts a small number of common passwords across
many accounts rather than repeatedly attacking a single account.

## Detection Objective

Identify a source IP generating multiple failed authentication attempts
against multiple user accounts within a short time window.

## MITRE ATT&CK

- **T1110** — Brute Force
- **T1110.003** — Password Spraying

## Platform

Microsoft Sentinel

## Data Source

Microsoft Entra ID / Azure AD Sign-in Logs

Primary table:

`SigninLogs`

## Detection Logic

The detection:

1. Reviews authentication activity from the previous hour.
2. Filters for failed authentication attempts.
3. Groups activity by source IP address.
4. Counts failed authentication attempts.
5. Counts the number of distinct targeted users.
6. Generates an alert when both thresholds are exceeded.

### Current thresholds

| Parameter | Value |
|---|---:|
| Time window | 1 hour |
| Failed attempts | ≥ 5 |
| Targeted users | ≥ 3 |

These values are example thresholds and should be tuned according to
the organization's authentication patterns.

## Why This Indicates Password Spraying

A password-spray attack commonly produces a pattern such as:

```text
Source IP
    |
    +---- User A → Failed login
    +---- User B → Failed login
    +---- User C → Failed login
    +---- User D → Failed login
    +---- User E → Failed login
