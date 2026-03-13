# ADR-003: Management Plane Protection

## Status
Accepted

## Context

Network devices must not expose management interfaces to untrusted networks.

## Decision

Management access allowed only from:

- VLAN30 (Management network)

Denied from:

- VLAN20 (Users)
- VLAN60 (Guest)

## Consequences

Firewall, switch and monitoring systems are accessible only from management hosts.

This reduces risk of compromise.