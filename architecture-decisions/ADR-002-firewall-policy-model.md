# ADR-002: Firewall Policy Model

## Status
Accepted

## Context

Firewall policy design must follow the principle of least privilege.

Users should only access required services.

Guest network must remain isolated.

## Decision

Implement explicit firewall rules:

VLAN20 → WAN (allow)  
VLAN20 → MGMT (deny)  
VLAN60 → WAN (allow)  
VLAN60 → INTERNAL (deny)

Logging is enabled for all deny policies.

## Consequences

Unauthorized lateral movement is prevented.

Firewall logs provide visibility into denied traffic.