# FortiGate 60E (FG)

## Device Role

The FortiGate firewall is the primary security enforcement point in the Enterprise Security Lab.

It performs:

- inter-VLAN routing  
- firewall policy enforcement  
- NAT to the internet  
- DHCP services  
- management plane protection  

The firewall separates internal security zones and enforces traffic control between them.

---

## Device Information

Device: FortiGate 60E  
Hostname: FG  

WAN connection:

ISP modem → FortiGate WAN

---

## Network Interfaces

| Interface | VLAN | Network | Purpose |
|-----------|------|--------|--------|
| VLAN20 | USERS | 10.10.20.1/24 | Client network |
| VLAN30 | MGMT | 10.10.30.1/24 | Infrastructure management |
| VLAN60 | GUEST | 10.10.60.1/24 | Guest internet access |

---

## DHCP Services

DHCP is provided by the firewall.

| VLAN | Range |
|-----|------|
| VLAN20 | 10.10.20.100–200 |
| VLAN60 | 10.10.60.100–200 |

DNS servers:

- 1.1.1.1  
- 8.8.8.8  

---

## Firewall Policy Model

| Source | Destination | Action |
|------|-------------|-------|
| USERS | INTERNET | ALLOW |
| GUEST | INTERNET | ALLOW |
| USERS | MGMT | DENY |
| GUEST | INTERNAL | DENY |

Default east-west traffic policy:

DENY

---

## Security Architecture Principles

The lab follows enterprise security design principles:

- VLAN network segmentation
- firewall enforced inter-VLAN routing
- guest network isolation
- management plane protection
- default-deny policy model

---

## Configuration Snapshot

The current configuration snapshot is stored in:

fortigate-config.tx
