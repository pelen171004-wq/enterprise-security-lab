# IP Addressing Plan

## Overview

The IP addressing model is designed to provide clear separation between management, user, server, guest, and monitoring functions.

Each network segment is assigned a dedicated subnet aligned with its operational role and security requirements.

The addressing approach prioritizes:

- readability
- predictable allocation
- easy troubleshooting
- clean segmentation boundaries
- future scalability

## Addressing Strategy

The environment uses private IPv4 addressing with one subnet assigned per VLAN.

Gateway addresses are assigned consistently at the first usable address in each subnet.

Infrastructure devices, servers, and critical services should use static addressing where appropriate, while client devices may use DHCP.

## Subnet Allocation

| Segment | VLAN | Subnet | Gateway | Addressing Method | Purpose |
|---|---:|---|---|---|---|
| Management | 10 | 10.10.10.0/24 | 10.10.10.1 | Static | Device and platform administration |
| Users | 20 | 10.10.20.0/24 | 10.10.20.1 | DHCP | Workstations and user endpoints |
| Servers | 30 | 10.10.30.0/24 | 10.10.30.1 | Static / DHCP reservation | Internal services and application hosts |
| Guest | 40 | 10.10.40.0/24 | 10.10.40.1 | DHCP | Guest wireless devices |
| SOC / Monitoring | 50 | 10.10.50.0/24 | 10.10.50.1 | Static | Monitoring and security tooling |
| Backup / Infrastructure | 60 | 10.10.60.0/24 | 10.10.60.1 | Static | Backup or infrastructure support services |

## Static Addressing Guidance

Static addressing should be used for:

- firewalls
- switches
- access points
- servers
- monitoring systems
- infrastructure management interfaces

Suggested examples:

| Hostname | Role | IP Address | Segment |
|---|---|---|---|
| fw01 | Firewall | 10.10.10.10 | Management |
| sw01 | Core / Access Switch | 10.10.10.11 | Management |
| ap01 | Wireless Access Point | 10.10.10.20 | Management |
| srv01 | DNS / DHCP / Directory | 10.10.30.10 | Servers |
| soc01 | Monitoring / SIEM / Dashboard | 10.10.50.10 | SOC / Monitoring |

## DHCP Guidance

DHCP should be used primarily in the following segments:

- user VLAN
- guest VLAN
- selected non-critical client environments

Recommended reservations may be used for:

- printers
- wireless infrastructure
- selected managed endpoints
- lab test devices requiring stable addressing

## Naming and Consistency

The addressing scheme follows a structured format where each VLAN aligns with the third octet.

Examples:

- VLAN 10 → 10.10.10.0/24
- VLAN 20 → 10.10.20.0/24
- VLAN 30 → 10.10.30.0/24

This improves readability and reduces operational confusion during troubleshooting.

## Operational Benefits

This IP plan supports:

- simpler fault isolation
- easier policy design
- predictable default gateways
- easier documentation maintenance
- cleaner troubleshooting workflows

## Summary

The addressing model is intentionally structured for operational clarity and security-oriented segmentation.

Each subnet has a clearly documented purpose, consistent gatewaying, and an allocation model that supports both administration and future growth.