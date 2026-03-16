# Firewall Policies

## Overview

The firewall policy model defines how communication between network zones is controlled.

The firewall acts as the primary enforcement point for inter-VLAN routing, segmentation, outbound internet access, and protection of internal resources.

The policy approach is based on default deny and explicit allow rules for required communication only.

## Policy Objectives

The firewall policy design aims to achieve the following:

- centralized enforcement of segmentation
- least-privilege access between zones
- protection of management interfaces
- isolation of guest and untrusted traffic
- control of server access paths
- support for logging and operational visibility

## Default Security Model

The default rule model is:

- deny traffic unless explicitly permitted
- allow only service-specific access
- restrict administrative access to management systems
- isolate guest traffic from internal resources
- limit outbound access where practical

## High-Level Policy Matrix

| Source Zone | Destination Zone | Allowed Services | Policy Intent |
|---|---|---|---|
| Management | Infrastructure Devices | SSH, HTTPS, platform management | Administrative access only |
| Users | Internet | HTTP, HTTPS, DNS, NTP | Standard outbound access |
| Users | Servers | Required application and service ports | Controlled internal service access |
| Guest | Internet | Required outbound services | Internet-only access |
| Guest | Internal Networks | None | Deny by policy |
| Servers | Internet | Approved update and support services | Limited outbound access |
| Monitoring | Firewall / Switch / Servers | Syslog, SNMP, API, telemetry | Monitoring visibility |
| Backup / Infrastructure | Servers | Backup and utility protocols | Restricted infrastructure access |

## Example Rule Set

| Rule ID | Source | Destination | Service | Action | Notes |
|---|---|---|---|---|---|
| R-01 | Management VLAN | Firewall Management IP | HTTPS, SSH | Allow | Admin access to firewall |
| R-02 | Management VLAN | Switch Management IP | HTTPS, SSH | Allow | Admin access to switch |
| R-03 | Management VLAN | AP Management IP | HTTPS, SSH | Allow | Admin access to wireless |
| R-04 | User VLAN | DNS Server | TCP/UDP 53 | Allow | Internal DNS resolution |
| R-05 | User VLAN | Internet | HTTP/HTTPS | Allow | General web access |
| R-06 | User VLAN | Server VLAN | Required app ports | Allow | Business application connectivity |
| R-07 | Guest VLAN | Internet | Outbound services | Allow | Internet-only access |
| R-08 | Guest VLAN | RFC1918 Internal Networks | Any | Deny | Internal isolation |
| R-09 | Monitoring VLAN | Firewall / Switch / Servers | Syslog, SNMP, API | Allow | Telemetry and visibility |
| R-10 | Any | Any | Any | Deny | Implicit or explicit cleanup rule |

## Administrative Access Control

Administrative access should be limited to approved systems in the management VLAN.

Best practice includes:

- permitting management protocols only from trusted admin hosts
- avoiding management exposure from user networks
- logging administrative access attempts
- restricting unnecessary management services

## Guest Isolation

The guest VLAN is treated as an untrusted segment.

The policy model for guest traffic is:

- allow outbound internet access
- deny access to all internal enterprise networks
- prevent access to management interfaces
- prevent lateral access to trusted zones

## Server Access Policy

Server access should be based on application need rather than broad zone trust.

This means:

- users access only required services
- servers do not expose unnecessary ports
- outbound internet access from servers is restricted
- management access to servers is separated from user access

## Logging and Visibility

Where supported, firewall rules should generate logs for:

- denied guest-to-internal access attempts
- management access attempts
- unusual inter-zone communication
- server access patterns
- policy violations or denied traffic of interest

This supports monitoring, troubleshooting, and incident analysis.

## Policy Governance

Firewall policy changes should be documented and reviewed.

For each new rule, document:

- business or technical reason
- source and destination zones
- required services and ports
- expected traffic direction
- risk or security impact
- review date if applicable

## Summary

The firewall policy model enforces segmented, least-privilege communication across the environment.

Its purpose is not only to permit required traffic, but also to define and protect trust boundaries across the lab.