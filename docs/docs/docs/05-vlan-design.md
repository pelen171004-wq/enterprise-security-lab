# VLAN Design

## Overview

The VLAN design is based on role-driven segmentation.

Each VLAN represents a distinct operational or security function and is separated to reduce unnecessary trust relationships between systems.

This approach improves:

- security
- manageability
- policy enforcement
- fault isolation
- traffic visibility

## Design Principles

The VLAN structure follows these principles:

- one functional role per VLAN where possible
- clear separation of management traffic
- isolation of guest and untrusted devices
- controlled access to server resources
- support for monitoring and operational workflows

## VLAN Allocation

| VLAN ID | Name | Purpose | Security Notes |
|---|---|---|---|
| 10 | Management | Administration of network and infrastructure devices | Restricted to authorized administrative access |
| 20 | Users | Standard user endpoints and workstation devices | Controlled access to internal and external services |
| 30 | Servers | Internal application and infrastructure services | Protected by firewall policies |
| 40 | Guest | Internet-only guest wireless access | No access to internal resources |
| 50 | SOC / Monitoring | Logging, dashboards, telemetry, and analysis | Receives operational and security data |
| 60 | Backup / Infrastructure | Backup, utility, or infrastructure support systems | Restricted to required service paths |

## VLAN Descriptions

### VLAN 10 - Management
This VLAN is dedicated to administration of firewalls, switches, wireless devices, and management interfaces.

Access should be limited to trusted administrative hosts only.

Protocols such as SSH, HTTPS, or platform-specific management services should be tightly restricted.

### VLAN 20 - Users
This VLAN supports user workstations and standard endpoint devices.

User traffic should be allowed only to approved internal services and necessary internet destinations.

Unrestricted east-west access should be avoided.

### VLAN 30 - Servers
This VLAN contains internal services such as DNS, DHCP, identity services, file services, or application systems.

Access to this VLAN should be granted only where a defined service dependency exists.

### VLAN 40 - Guest
This VLAN is intended for guest wireless or other untrusted temporary devices.

The security model for this VLAN is internet-only access with complete isolation from internal enterprise resources.

### VLAN 50 - SOC / Monitoring
This VLAN supports monitoring systems, logging platforms, dashboards, or analysis hosts.

It provides operational and security visibility and may receive traffic telemetry or forwarded logs from infrastructure components.

### VLAN 60 - Backup / Infrastructure
This VLAN is reserved for infrastructure support functions such as backup targets, utility services, staging systems, or similar internal technical roles.

Access should be restricted to explicitly required systems and flows.

## Routing and Policy Model

Inter-VLAN communication is not permitted by default.

Traffic between VLANs is routed through the firewall, where security policies determine which flows are allowed.

This provides:

- centralized enforcement
- stronger segmentation control
- easier auditability
- consistent policy application

## Wireless Mapping

Wireless networks should map to the correct VLANs according to trust level.

Examples:

- corporate SSID → user VLAN
- guest SSID → guest VLAN

This ensures that wireless devices inherit the appropriate security policy based on network role.

## Operational Considerations

The VLAN model should remain simple, clearly documented, and aligned with real operational needs.

When new VLANs are introduced, the following should be documented:

- business or technical purpose
- subnet assignment
- default gateway
- expected traffic flows
- policy requirements
- management implications

## Summary

The VLAN design supports an enterprise-style segmented environment with clear trust boundaries, centralized policy control, and improved operational clarity.

Each VLAN exists for a defined reason and is aligned with both security and manageability goals.