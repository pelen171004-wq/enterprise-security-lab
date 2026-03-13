# THREAT-001: Network Zone Threat Model

## Status
Active

## Scope

This threat model covers the current Enterprise Security Lab network zones:

- VLAN20 – USERS
- VLAN30 – MGMT
- VLAN60 – GUEST

Planned future zones:

- VLAN40 – SOC
- VLAN50 – SERVERS
- VLAN70 – BACKUP

---

## Security Objective

The objective is to reduce attack surface, limit lateral movement, and protect the management plane from untrusted endpoints.

---

## Threat 1 – User to Management Access

### Description
A compromised user endpoint attempts to reach management interfaces of security or network devices.

### Risk
If successful, an attacker may gain access to firewall or switch management and compromise the environment.

### Mitigation
- Dedicated management VLAN
- Users → Management deny policy
- FortiGate trusted host configuration
- Restricted management access model

---

## Threat 2 – Guest to Internal Access

### Description
An untrusted guest device attempts to access internal infrastructure or security devices.

### Risk
Unauthorized internal access, reconnaissance, malware spread.

### Mitigation
- Guest VLAN isolated from internal networks
- Guest → Internal deny policy
- Guest internet-only design
- Local-in deny for guest traffic to FortiGate

---

## Threat 3 – Excessive Trust Between Zones

### Description
Too many broad allow rules create unnecessary trust between VLANs.

### Risk
Lateral movement becomes easier after compromise.

### Mitigation
- Explicit firewall policies
- Least privilege traffic model
- Zone-based segmentation
- Default-deny mindset for east-west traffic

---

## Threat 4 – Weak Visibility

### Description
Traffic anomalies or malicious activity occur without logging or monitoring visibility.

### Risk
Delayed incident detection and limited troubleshooting capability.

### Planned Mitigation
- SOC / monitoring VLAN
- Traffic logs
- Session troubleshooting workflow
- Security monitoring stack
- Centralized logging

---

## Assumptions

- FortiGate is the primary policy enforcement point
- CBS250 delivers VLAN separation to endpoints
- Management access is limited to the MGMT zone
- Guest devices are untrusted by design

---

## Conclusion

This threat model supports the segmented design of the lab and justifies the use of restricted traffic flows between zones.