# Security Control Matrix

This document maps implemented security controls in the Enterprise Security Lab architecture.

---

## Network Segmentation

Control objective: reduce lateral movement and isolate trust zones.

Implementation:

- VLAN20 USERS
- VLAN30 MGMT
- VLAN60 GUEST
- Planned zones: SOC / SERVERS / BACKUP

Enforcement device:

- FortiGate 60E
- Cisco CBS250 VLAN switching

Security benefit:

- Isolation between network segments
- Reduced blast radius
- Controlled traffic flows

---

## Firewall Policy Enforcement

Control objective: explicit allow/deny traffic model.

Implementation:

- Inter-VLAN firewall policies
- Default deny mindset
- Zone-based traffic control

Examples:

USERS → WAN = allow
USERS → MGMT = deny
GUEST → INTERNAL = deny

Security benefit:

- Prevent unauthorized internal access
- Limit attack surface
- Improve traffic visibility

---

## Management Plane Protection

Control objective: protect administrative interfaces.

Implementation:

- VLAN30 management network
- Trusted hosts on FortiGate
- Local-in policy restrictions

Security benefit:

- Reduced exposure of infrastructure devices
- Protection against unauthorized administrative access

---

## Guest Network Isolation

Control objective: isolate untrusted devices.

Implementation:

- VLAN60 guest network
- Guest → internet only
- Guest blocked from internal infrastructure

Security benefit:

- Protection against untrusted endpoints
- Reduced risk of lateral movement

---

## Observability (planned)

Control objective: improve security visibility.

Planned implementation:

- SOC monitoring VLAN
- Traffic logging
- SIEM integration
- Central log collection

Security benefit:

- Faster detection of suspicious activity
- Improved incident response

---

## Architecture principle

The lab follows a layered security model:

- segmentation
- explicit traffic control
- management plane isolation
- monitoring readiness