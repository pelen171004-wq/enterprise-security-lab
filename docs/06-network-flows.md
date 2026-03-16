# Network Flows

## Overview

The network flow model defines how traffic moves between security zones in the Enterprise Security Lab.

Documenting expected communication paths helps with:

- firewall rule design
- troubleshooting
- security review
- architecture clarity

The environment follows a **default deny** approach where traffic is allowed only when explicitly required.

## Zone Communication Model

The network is divided into multiple zones with controlled communication paths.

| Source Zone | Destination Zone | Typical Services | Policy |
|---|---|---|---|
| Management | Infrastructure Devices | SSH, HTTPS | Allow |
| Users | Internet | HTTP, HTTPS, DNS | Allow |
| Users | Servers | Application ports | Allow when required |
| Users | Management | Any | Deny |
| Guest | Internet | HTTP, HTTPS | Allow |
| Guest | Internal Networks | Any | Deny |
| Servers | Internet | Updates, repositories | Allow when required |
| Monitoring | Infrastructure | Syslog, SNMP | Allow |

## Traffic Matrix

| Flow ID | Source | Destination | Port | Purpose | Action |
|---|---|---|---|---|---|
| F-01 | Management | Firewall | 443 / 22 | Admin access | Allow |
| F-02 | Management | Switch | 443 / 22 | Admin access | Allow |
| F-03 | Users | DNS Server | 53 | DNS resolution | Allow |
| F-04 | Users | Internet | 80 / 443 | Web access | Allow |
| F-05 | Users | Application Server | App specific | Application usage | Allow |
| F-06 | Guest | Internet | Any required | Internet access | Allow |
| F-07 | Guest | Internal networks | Any | Internal access | Deny |
| F-08 | Monitoring | Firewall | Syslog | Logging | Allow |

## Design Intent

The goal of the flow model is to ensure:

- segmentation between trust zones
- minimal exposure of services
- clear documentation of allowed communication paths
- easier firewall policy implementation

## Summary

Documenting network flows provides a clear map of how systems interact and supports both security enforcement and operational troubleshooting.