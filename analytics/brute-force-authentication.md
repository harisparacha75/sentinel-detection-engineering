# Brute Force Authentication Detection

## Overview

This detection identifies potential brute-force authentication activity
by detecting a high volume of failed authentication attempts originating
from the same source IP address.

Unlike password spraying, which typically targets many accounts with a
small number of attempts per account, traditional brute-force activity
generally produces repeated authentication attempts against the same
account or a limited number of accounts.

## Detection Objective

Identify authentication sources generating a high number of failed
authentication attempts within a defined time window.

## MITRE ATT&CK

- **T1110** — Brute Force

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
3. Groups authentication failures by source IP address.
4. Counts the total number of failed attempts.
5. Identifies targeted accounts.
6. Identifies applications involved.
7. Generates a detection when the failed-attempt threshold is exceeded.

### Current threshold

| Parameter | Value |
|---|---:|
| Time window | 1 hour |
| Failed attempts | ≥ 10 |

These values are example thresholds and should be tuned according to
the organization's authentication baseline.

## Attack Pattern

A traditional brute-force attack may produce activity such as:

```text
Source IP
    |
    └── User A
         ├── Failed attempt
         ├── Failed attempt
         ├── Failed attempt
         ├── Failed attempt
         └── ... repeated attempts
