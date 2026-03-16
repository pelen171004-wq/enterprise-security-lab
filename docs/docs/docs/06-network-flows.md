# Network Flows

## Overview

The network flow model defines how traffic is expected to move between security zones.

Its purpose is to document approved communication paths, reduce ambiguity, and support security enforcement through the firewall.

This model improves:

- architecture clarity
- firewall rule design
- troubleshooting consistency
- auditability
- change control

## Design Principles

Traffic flows are based on the following principles:

- deny by default unless explicitly required
- allow only service-driven communication
- separate trusted, semi-trusted, and untrusted zones
- ensure management access is tightly controlled
- prevent unnecessary east-west communication

## Zone Flow Summary

| Source Zone | Destination Zone | Typical Services | Expected Action | Notes |
|---|---|---|---|---|
| Management | Infrastructure Devices | SSH, HTTPS, management protocols | Allow | Restricted to admin systems only |
| Users | Internet | HTTP, HTTPS, DNS, NTP | Allow | Standard outbound connectivity |
| Users | Servers | Application-specific ports | Allow as required | Only for approved services |
| Users | Management | Any | Deny | Users should not manage infrastructure |
| Guest | Internet | HTTP, HTTPS, DNS | Allow | Internet-only access |
| Guest | Internal Networks | Any | Deny | Complete internal isolation |
| Servers | Internet | Updates, package repositories, NTP, DNS | Allow as required | Limited and controlled |
| Servers | Users | Application responses only | Allow as required | Should not be broad or unrestricted |
| Monitoring | Infrastructure / Firewall / Servers | Syslog, SNMP, telemetry, API | Allow | Operational visibility use case |
| Backup / Infrastructure | Servers | Backup protocols, file transfer | Allow as required | Restricted to defined systems |

## Detailed Flow Intent

### Management to Infrastructure
Administrative access is permitted only from approved management hosts to infrastructure systems.

Typical protocols include:

- SSH
- HTTPS
- management UI access
- platform-specific administration services

This flow must be tightly restricted and logged where possible.

### Users to Internet
User endpoints require standard outbound internet access for browsing, updates, and cloud-connected services.

This should generally include:

- HTTP / HTTPS
- DNS
- NTP

Other outbound traffic should be reviewed and allowed only where justified.

### Users to Servers
Users may access internal servers only when a business or technical dependency exists.

Examples:

- DNS queries
- directory services
- internal application access
- file services

This flow should not be open broadly across all ports.

### Guest to Internet
Guest devices are considered untrusted and should be allowed outbound internet access only.

No access to management, servers, users, or monitoring systems should be permitted.

### Monitoring to Infrastructure
Monitoring and logging systems may need access to infrastructure or receive telemetry from devices.

Examples include:

- syslog
- SNMP
- API-based polling
- agent-based monitoring

These flows should be documented clearly to support operations and incident response.

## Traffic Matrix

| Flow ID | Source | Destination | Service / Port | Purpose | Action |
|---|---|---|---|---|---|
| F-01 | Management | Firewall | HTTPS / SSH | Administrative access | Allow |
| F-02 | Management | Switch | HTTPS / SSH | Administrative access | Allow |
| F-03 | Management | Access Point | HTTPS / SSH | Administrative access | Allow |
| F-04 | Users | DNS Server | TCP/UDP 53 | Name resolution | Allow |
| F-05 | Users | Internet | TCP 80/443 | Web access | Allow |
| F-06 | Users | Application Server | App-specific ports | Business application access | Allow |
| F-07 | Guest | Internet | Required outbound services | Internet access | Allow |
| F-08 | Guest | Internal Networks | Any | Internal access attempt | Deny |
| F-09 | Monitoring | Firewall / Switch / Servers | Syslog / SNMP / API | Visibility and telemetry | Allow |
| F-10 | Backup | Servers | Backup-specific ports | Backup operations | Allow |

## Operational Guidance

When introducing a new system or VLAN, its flows should be documented before broad access is allowed.

Each new flow should define:

- source zone
- destination zone
- required ports or protocols
- business or technical justification
- expected direction
- logging or monitoring requirements

## Summary

The network flow model documents intended communication patterns and supports a security-first architecture.

By defining approved paths explicitly, the lab becomes easier to secure, troubleshoot, and maintain.