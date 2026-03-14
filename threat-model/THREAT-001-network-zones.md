# THREAT-001: Network Zone Threat Model

## Status
Active

---

## Scope

This threat model covers the current Enterprise Security Lab network zones.

### Current Zones

- VLAN20 – USERS
- VLAN30 – MGMT
- VLAN60 – GUEST

### Planned Future Zones

- VLAN40 – SOC
- VLAN50 – SERVERS
- VLAN70 – BACKUP

These zones form the foundation of the segmented security architecture implemented in the lab.

---

## Security Objective

The primary objective of this network design is to:

- reduce attack surface
- limit lateral movement
- isolate untrusted endpoints
- protect the management plane

All traffic between zones is inspected and controlled by the FortiGate firewall.

The architecture follows a **Zero Trust inspired model** where traffic must be explicitly allowed.

---

## Threat 1 – User to Management Access

### Description

A compromised user endpoint attempts to reach management interfaces of security or network devices.

Examples:

- FortiGate management interface
- Switch management interface

### Risk

If successful, an attacker could gain administrative access to security infrastructure and compromise the environment.

### Mitigation

- Dedicated management VLAN
- Users → Management deny firewall policy
- FortiGate trusted host configuration
- Restricted management access model

---

## Threat 2 – Guest to Internal Access

### Description

An untrusted guest device attempts to access internal infrastructure or security devices.

Guest networks should never have visibility into internal services.

### Risk

Possible outcomes include:

- internal reconnaissance
- service enumeration
- malware propagation

### Mitigation

- Guest VLAN isolated from internal networks
- Guest → Internal deny firewall policy
- Guest internet-only design
- Local-in deny policy for guest traffic targeting FortiGate

---

## Threat 3 – Excessive Trust Between Zones

### Description

Overly permissive firewall policies can create unnecessary trust relationships between security zones.

### Risk

After a single host compromise, attackers may move laterally across the network.

### Mitigation

- Explicit firewall policies
- Least privilege traffic model
- Zone-based segmentation
- Default-deny approach for east-west traffic

---

## Threat 4 – Weak Visibility

### Description

Network anomalies or malicious activity may occur without sufficient monitoring or logging.

### Risk

Delayed incident detection and limited troubleshooting capability.

### Planned Mitigation

Future monitoring improvements include:

- SOC / monitoring VLAN
- firewall traffic logging
- session troubleshooting workflow
- security monitoring stack
- centralized logging

---

## Assumptions

The threat model assumes the following architectural conditions:

- FortiGate is the primary policy enforcement point
- Cisco CBS250 provides VLAN segmentation
- Management access is limited to the MGMT VLAN
- Guest devices are treated as untrusted endpoints
- Inter-VLAN traffic is inspected by firewall policy

---

## Conclusion

This threat model supports the segmented architecture used in the Enterprise Security Lab.

The combination of VLAN segmentation, firewall policy enforcement and management plane isolation significantly reduces the attack surface and limits potential lateral movement within the environment.