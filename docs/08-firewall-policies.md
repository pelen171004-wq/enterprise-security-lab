# Firewall Policies

## Overview

The firewall is the central security enforcement point in the Enterprise Security Lab.

It performs:

- inter-VLAN routing
- traffic inspection
- access control
- NAT for outbound connectivity
- logging and monitoring support

The firewall policy model follows a **default deny** approach.

Traffic between zones is only allowed when explicitly required.

## Policy Design Principles

Firewall rules follow these principles:

- least privilege access
- minimal exposed services
- separation between trust zones
- administrative access restricted to management network
- logging of important events

## High-Level Policy Matrix

| Source Zone | Destination Zone | Allowed Services | Policy Intent |
|---|---|---|---|
| Management | Infrastructure | SSH, HTTPS | Admin access |
| Users | Internet | HTTP, HTTPS, DNS | Standard outbound access |
| Users | Servers | Application ports | Application access |
| Guest | Internet | HTTP, HTTPS | Internet-only access |
| Guest | Internal Networks | None | Deny |
| Monitoring | Infrastructure | Syslog, SNMP | Monitoring visibility |

## Example Firewall Rules

| Rule ID | Source | Destination | Service | Action |
|---|---|---|---|---|
| R-01 | Management VLAN | Firewall | HTTPS, SSH | Allow |
| R-02 | Management VLAN | Switch | HTTPS, SSH | Allow |
| R-03 | Users VLAN | Internet | HTTP/HTTPS | Allow |
| R-04 | Users VLAN | DNS Server | DNS | Allow |
| R-05 | Guest VLAN | Internet | HTTP/HTTPS | Allow |
| R-06 | Guest VLAN | Internal Networks | Any | Deny |
| R-07 | Monitoring VLAN | Firewall | Syslog | Allow |
| R-08 | Any | Any | Any | Deny |

## Administrative Access Control

Administrative access should only be allowed from the management VLAN.

Recommended controls:

- allow SSH / HTTPS only
- disable unused services
- restrict access by IP where possible
- log administrative access attempts

## Guest Isolation

Guest devices must be isolated from internal resources.

Guest traffic policy:

- allow internet access
- deny internal RFC1918 networks
- deny management access

## Logging

Firewall rules should log important events such as:

- denied connections
- management access
- unusual traffic patterns
- guest network violations

This helps with monitoring and incident analysis.

## Summary

The firewall policy model enforces segmentation, protects infrastructure systems, and ensures that communication between zones is controlled and documented.