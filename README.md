## Log Analysis & Security Investigation

## Overview

This project demonstrates a basic security investigation of Linux authentication logs. The goal was to identify repeated failed login attempts, review successful logins, and determine whether the activity showed signs of suspicious authentication behavior.

## Scenario

A company noticed unusual login activity involving an employee account. As a junior SOC analyst, I was asked to review the authentication logs and determine whether there were any signs of suspicious login attempts.

### Investigation Questions

- Which accounts were targeted?
- How many login attempts failed?
- Which IP addresses were involved?
- Were any suspicious login attempts successful?
- What pattern can be observed from the activity?

- ## Tools & Commands

- Kali Linux
- SSH authentication logs
- `grep`
- `awk`
- `sort`
- `uniq`

## Investigation & Findings

### 1. Failed Login Attempts

The authentication log was filtered to identify failed password attempts.

Five failed login attempts were identified for the `analyst` account from `185.220.101.42`.

Three failed login attempts were identified for the `admin` account from `203.0.113.45`.

### 2. Failed Logins by IP Address

| Source IP | Failed Attempts | Target Account |
|---|---:|---|
| `185.220.101.42` | 5 | `analyst` |
| `203.0.113.45` | 3 | `admin` |

The repeated attempts from the same IP addresses may indicate password-guessing activity and warranted further investigation.

### 3. Successful Logins

Two successful logins were identified for the `analyst` account.

Both successful logins originated from `192.168.1.25`.

No successful login from the two IP addresses associated with the repeated failed attempts was observed in the provided logs.

### 4. Authentication Timeline

The authentication events were reviewed chronologically:

- **08:12** — Five failed login attempts against `analyst` from `185.220.101.42`.
- **08:15** — Successful login for `analyst` from `192.168.1.25`.
- **09:03** — Three failed login attempts against `admin` from `203.0.113.45`.
- **09:10** — Successful login for `analyst` from `192.168.1.25`.

## Evidence

Screenshots documenting the investigation are available in the [`evidence`](./evidence) folder.

- `failed-login-attempts.png` — Failed authentication attempts
- `failed-logins-by-ip.png` — Failed attempts grouped by source IP
- `successful-logins.png` — Successful authentication events
- `authentication-timeline.png` — Combined authentication timeline

## Conclusion

Repeated failed authentication attempts were identified from two source IP addresses and may indicate password-guessing activity.

No successful authentication from those IP addresses was observed in the provided logs. Further investigation would be required to determine whether the activity was malicious.

## Skills Demonstrated

- Linux command-line investigation
- Authentication log analysis
- Identifying failed and successful login activity
- Basic IP-based investigation
- Timeline analysis
- Evidence collection and documentation
- Security-focused analytical reasoning
