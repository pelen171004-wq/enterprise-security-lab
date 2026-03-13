# ADR-001: Network Segmentation Model

## Status
Accepted

## Context

The lab environment contains multiple network zones including:

- User network
- Management network
- Guest network
- Server network

Without segmentation, user devices could access management interfaces or critical infrastructure.

## Decision

Implement VLAN-based segmentation enforced by FortiGate firewall.

Zones:

- VLAN20: Users
- VLAN30: Management
- VLAN60: Guest

Firewall rules enforce:

Users → Management = DENY  
Guest → Internal = DENY  
Users → WAN = ALLOW

## Consequences

Improved security isolation.

Guest devices cannot reach internal infrastructure.

Management plane is protected.

This model aligns with Zero Trust network design principles.
