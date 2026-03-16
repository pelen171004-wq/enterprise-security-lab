# Architecture

## High-Level Architecture

The Enterprise Security Lab is designed as a segmented network environment with centralized traffic control and clearly separated trust zones.

The firewall acts as the primary security enforcement point and controls inter-VLAN communication between internal network segments and external connectivity.

This design reflects a simplified enterprise model where segmentation, visibility, and controlled access are prioritized over flat network design.

## Core Architectural Principles

The environment follows these architectural principles:

- centralized policy enforcement through the firewall
- dedicated management access for infrastructure administration
- segmentation of users, servers, guests, and infrastructure services
- least-privilege communication between network zones
- operational visibility for monitoring and troubleshooting

## Security Boundary

The firewall represents the primary security boundary in the environment.

Its responsibilities include:

- inter-VLAN routing
- traffic inspection
- policy enforcement
- NAT for outbound connectivity
- access control between internal zones

## Network Zones

The lab is divided into logical security zones.

### Management Zone
Used for administration of network devices, infrastructure services, and platform management interfaces.

This zone should be restricted to authorized administrative access only.

### User Zone
Represents standard client endpoints and workstation devices.

User traffic is allowed only to approved destinations and services.

### Server Zone
Contains internal infrastructure services and application hosts.

Access to this zone is controlled according to service requirements.

### Guest Zone
Provides internet-only access for untrusted or temporary devices.

This zone must remain isolated from internal enterprise resources.

### SOC / Monitoring Zone
Used for monitoring, security visibility, logs, dashboards, or analysis systems.

This zone improves operational awareness and supports incident investigation.

## Routing Model

The routing model is based on firewall-controlled inter-VLAN routing.

This means that communication between internal network segments is not switched freely at Layer 3 by the access switch. Instead, traffic is sent to the firewall where policy decisions are applied.

This approach improves control, segmentation, and auditability.

## Design Rationale

The architecture was intentionally designed to demonstrate enterprise-oriented security thinking.

Key design decisions include:

- avoiding flat network structure
- isolating management traffic
- separating guest access from trusted networks
- enforcing policy at a central control point
- documenting architecture in a way that supports operations and troubleshooting

## Architectural Summary

The lab models a small enterprise-style environment with:

- segmented VLAN architecture
- centralized firewall policy enforcement
- isolated guest access
- dedicated management paths
- operational focus on security monitoring and incident readiness