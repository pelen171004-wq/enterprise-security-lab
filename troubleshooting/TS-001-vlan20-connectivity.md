# TS-001 VLAN20 Connectivity Investigation

## Problem

Client in VLAN20 could not reach external DNS services.

Symptoms:

- ping 1.1.1.1 OK
- nslookup google.com FAIL

---

## Investigation

Firewall session table inspection:

diagnose sys session filter src 10.10.20.100
diagnose sys session list

Result:

SNAT 10.10.20.100 -> 192.168.0.108
policy_id=6

---

## Packet Capture

diagnose sniffer packet any "host 10.10.20.100" 4

Observed traffic:

10.10.20.100 -> 1.1.1.1:53
1.1.1.1 -> 10.10.20.100

---

## Root Cause

DNS configuration on client incorrectly set.

---

## Resolution

Correct DNS servers configured:

1.1.1.1  
8.8.8.8