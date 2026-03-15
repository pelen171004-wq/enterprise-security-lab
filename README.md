# Enterprise Security Lab

![Firewall](https://img.shields.io/badge/Firewall-FortiGate-red)
![Switch](https://img.shields.io/badge/Switch-Cisco_CBS250-blue)
![Architecture](https://img.shields.io/badge/Architecture-Segmented-green)
![Security](https://img.shields.io/badge/Security-Zero_Trust-orange)
![Project](https://img.shields.io/badge/Project-Enterprise_Lab-purple)

Enterprise-style **Network Security Lab** demonstrating firewall architecture, VLAN segmentation and security design principles.

This repository documents a practical home lab focused on:

- network security engineering
- firewall policy architecture
- VLAN segmentation
- traffic troubleshooting
- infrastructure security design
- threat modeling

The project simulates a **segmented enterprise network** built around a FortiGate NGFW and Cisco CBS250 switch.

---

# Live Lab Portal

Interactive documentation portal:

https://pelen171004-wq.github.io/enterprise-security-lab/

The portal contains:

- architecture diagrams
- device configuration documentation
- security architecture decisions
- threat modeling
- troubleshooting playbooks
- interactive topology

---

# Network Architecture

![Enterprise Security Lab Architecture](lab-architecture-v2.jpg)

### Simplified Topology

Internet  
│  
Vodafone ISP Modem  
│  
FortiGate 60E (NGFW)  
│  
Cisco CBS250 (Core Switch)  
│  
├── VLAN20 – Users Network  
├── VLAN30 – Management Network  
└── VLAN60 – Guest Network  

### Planned Network Zones

Future expansion of the lab includes additional enterprise infrastructure zones:

- VLAN40 – SOC / Security Monitoring
- VLAN50 – Server Infrastructure
- VLAN70 – Backup Systems

---

# Network Security Zones

| Zone | Description |
|-----|-------------|
| Internet | Untrusted external network |
| Firewall | Primary security enforcement point |
| Users VLAN | Internal client devices |
| Guest VLAN | Internet-only isolated network |
| Management VLAN | Administrative device access |
| Server Zone (planned) | Infrastructure services |
| Backup Zone (planned) | Backup infrastructure |

---

# Infrastructure Components

## FortiGate 60E

Next-Generation Firewall responsible for:

- inter-VLAN routing
- firewall policy enforcement
- NAT to the internet
- DHCP services
- traffic inspection

## Cisco CBS250

Layer 2 switch responsible for:

- VLAN segmentation
- trunk connectivity to firewall
- endpoint access ports
- infrastructure connectivity

### Technologies Used

- VLAN segmentation
- firewall policy enforcement
- NAT
- DHCP
- packet inspection
- traffic analysis

---

# Skills Demonstrated

This project demonstrates practical experience in:

- network segmentation design
- firewall policy architecture
- infrastructure security design
- network troubleshooting
- security monitoring architecture
- threat modeling
- security frameworks alignment
- architecture documentation

---

# Security Architecture

Key security design principles implemented in this lab:

- VLAN-based network segmentation
- firewall enforced inter-VLAN routing
- guest network isolation
- management plane protection
- explicit allow / deny firewall model
- default deny east-west traffic

The architecture follows a **least privilege network model** where traffic must be explicitly permitted.

---

# Firewall Policy Matrix

Traffic between VLANs is inspected by the FortiGate firewall.

| Source Zone | Destination Zone | Service | Action | Description |
|-------------|------------------|--------|--------|-------------|
| Users VLAN (20) | Internet | ANY | ALLOW | Standard user internet access |
| Guest VLAN (60) | Internet | ANY | ALLOW | Guest internet access |
| Users VLAN (20) | Management VLAN (30) | ANY | DENY | Protect management plane |
| Guest VLAN (60) | Users VLAN (20) | ANY | DENY | Prevent lateral movement |
| Guest VLAN (60) | Management VLAN (30) | ANY | DENY | Block infrastructure access |
| Any Internal VLAN | Any Internal VLAN | ANY | DENY | Default deny inter-VLAN |

This policy model follows a **Zero Trust inspired segmentation approach**.

---

# Security Controls Implemented

| Control | Implementation |
|-------|----------------|
| Network Segmentation | VLAN architecture on Cisco CBS250 |
| Firewall Enforcement | FortiGate NGFW policy model |
| Guest Isolation | Dedicated internet-only VLAN |
| Management Protection | Separate management network |
| Inter-VLAN Security | Firewall enforced traffic filtering |
| Threat Modeling | Documented attack surface analysis |
| Security Architecture | Zero Trust design principles |

---

# Device Configuration Repository

Sanitized configuration snapshots and device documentation are stored in the repository.

## Firewall

- [FortiGate Configuration Notes](configs/fortigate/README.md)
- [FortiGate Config Snapshot](configs/fortigate/fortigate-config.txt)

## Switching

- [Cisco CBS250 Device Notes](configs/cisco-cbs250/README.md)
- [SWA Config Snapshot](configs/cisco-cbs250/swa-config.txt)

## Troubleshooting

- [Troubleshooting Notes](troubleshooting/README.md)

Configuration snapshots document:

- VLAN architecture
- firewall policies
- routing
- NAT configuration
- management access design

---

# Attack Surface Overview

Potential attack vectors and mitigations.

| Attack Surface | Threat | Mitigation |
|---------------|-------|-----------|
| Internet Edge | Port scanning | Firewall policy enforcement |
| Guest Network | Untrusted devices | VLAN isolation |
| User Network | Compromised endpoint | Inter-VLAN firewall rules |
| Management Plane | Unauthorized access | Management VLAN isolation |

Full documentation:

https://pelen171004-wq.github.io/enterprise-security-lab/attack-surface.html

---

# Firewall Traffic Analysis

Firewall behaviour and segmentation were validated using FortiGate diagnostic tools.

Troubleshooting techniques used in this lab include:

- FortiGate debug flow
- session table inspection
- packet capture analysis
- NAT verification

These tools allow verification of:

- firewall policy enforcement
- NAT translation
- traffic direction
- session state

---

# Threat Model

Threat modeling identifies potential attack scenarios across network zones.

| Document | Description |
|--------|-------------|
| [THREAT-001 Network Zones](threat-model/THREAT-001-network-zones.md) | Network segmentation threat analysis |

Threat modeling supports the segmented architecture and security controls implemented in this lab.

---

# Troubleshooting & Operations

Operational troubleshooting includes:

- connectivity debugging
- firewall policy validation
- packet flow inspection
- session analysis
- network diagnostics

Troubleshooting playbook:

https://pelen171004-wq.github.io/enterprise-security-lab/troubleshooting.html

---

# Security Framework Alignment

The architecture aligns with common industry security frameworks.

### Zero Trust Architecture

- network segmentation
- explicit trust boundaries
- least privilege traffic model

### CIS Critical Security Controls

- secure network infrastructure
- network monitoring
- traffic inspection

Architecture decision documentation:

https://pelen171004-wq.github.io/enterprise-security-lab/architecture-decisions.html

---

# Lab Roadmap

Future development phases.

## Phase 1 – Core Network Security (Current)

- FortiGate deployment
- Cisco switching
- VLAN segmentation
- guest network isolation
- management network
- firewall policy enforcement

## Phase 2 – Security Monitoring

- SOC VLAN
- centralized logging
- SIEM integration
- network monitoring

## Phase 3 – Infrastructure Expansion

- server infrastructure zone
- backup infrastructure
- security service segmentation

## Phase 4 – Enterprise Features

- firewall high availability
- automated configuration backups
- security incident response playbooks