# Security Architecture Decision Record – Network Segmentation

## Decision

The lab uses segmented VLAN-based network design with FortiGate as the primary enforcement point between trust zones.

---

## Context

The goal of this lab is to simulate enterprise-style network security architecture.

A flat network would not reflect real-world security requirements.
To model secure design principles, the environment is divided into dedicated trust zones.

Zones currently implemented or planned:

- VLAN20 – USERS
- VLAN30 – MGMT
- VLAN40 – SOC (planned)
- VLAN50 – SERVERS (planned)
- VLAN60 – GUEST
- VLAN70 – BACKUP (planned)

---

## Why this decision was made

Segmented architecture improves:

- security boundaries
- access control
- visibility
- troubleshooting clarity
- reduction of lateral movement

This also allows firewall rules to be written per zone instead of broad network-wide access.

---

## Enforcement model

FortiGate acts as the main policy enforcement point.

Examples:

- USERS → WAN = allow
- USERS → MGMT = deny
- GUEST → INTERNAL = deny
- MGMT → infrastructure = controlled access

CBS250 is used as the switching layer to deliver VLAN separation to endpoints and future infrastructure.

---

## Security benefits

- management plane isolation
- guest isolation
- reduced blast radius
- better auditability
- simpler policy review

---

## Trade-offs

Segmented design introduces:

- more firewall rules
- more troubleshooting steps
- higher design complexity

However, the security and operational benefits outweigh the complexity.

---

## Status

Implemented:
- VLAN20 Users
- VLAN30 Management
- VLAN60 Guest
- FortiGate inter-zone enforcement baseline
- CBS250 VLAN switching baseline

Planned:
- SOC zone
- Server zone
- Backup zone
- wireless integration
- monitoring stack

---

## Conclusion

Network segmentation is a foundational architectural decision in this lab and aligns with enterprise security engineering practices.