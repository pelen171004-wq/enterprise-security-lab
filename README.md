# Enterprise Security Lab

![Firewall](https://img.shields.io/badge/Firewall-FortiGate-red)
![Switch](https://img.shields.io/badge/Switch-Cisco_CBS250-blue)
![Architecture](https://img.shields.io/badge/Architecture-Segmented-green)
![Security](https://img.shields.io/badge/Security-Zero_Trust-orange)
![Project](https://img.shields.io/badge/Project-Enterprise_Lab-purple)

Enterprise-style Network Security Lab demonstrating firewall architecture, VLAN segmentation and security design principles.

This repository documents a practical home lab focused on network security engineering, firewall policy design and traffic troubleshooting.

---

# Live Lab Portal

Interactive documentation portal:

https://pelen171004-wq.github.io/enterprise-security-lab/

The portal contains:

- Architecture diagrams
- Device configuration documentation
- Security design decisions
- Threat modeling
- Troubleshooting playbooks

---

# Network Architecture

![Enterprise Security Lab Architecture](lab-architecture-v2.jpg)

Simplified topology:

Internet  
│  
Vodafone ISP Modem  
│  
FortiGate 60E (NGFW)  
│  
Cisco CBS250 (Core Switch)  
│  
VLAN20 – Users Network  
VLAN30 – Management Network  
VLAN60 – Guest Network  

Planned zones:

VLAN40 – SOC Monitoring  
VLAN50 – Server Zone  
VLAN70 – Backup Zone  

---

# Network Security Zones

Internet  
Untrusted external network

Firewall  
Primary security enforcement point

Users VLAN  
Standard internal client network

Guest VLAN  
Isolated internet-only network

Management VLAN  
Administrative access to infrastructure

Server Zone (planned)  
Infrastructure services

Backup Zone (planned)  
Backup systems

---

# Infrastructure Components

FortiGate 60E  
Next-Generation Firewall performing routing, NAT and policy enforcement

Cisco CBS250  
Layer 2 switching and VLAN segmentation

Technologies used:

- VLAN segmentation
- Firewall policies
- NAT
- DHCP
- Network troubleshooting tools

---

# Skills Demonstrated

This project demonstrates practical experience in:

- Network segmentation design
- Firewall policy architecture
- Infrastructure security design
- Network troubleshooting
- Security monitoring architecture
- Threat modeling
- Security frameworks alignment
- Architecture documentation

---

# Security Architecture

Key security principles implemented:

- VLAN-based network segmentation
- Inter-VLAN firewall enforcement
- Guest network isolation
- Management plane protection
- Zero Trust inspired architecture
- Explicit allow / deny firewall policies
- Default-deny security model

---

# Firewall Policy Matrix

The firewall enforces strict segmentation between network zones.

Traffic between VLANs must pass through the FortiGate firewall where security policies are evaluated.

| Source Zone | Destination Zone | Service | Action | Description |
|-------------|------------------|--------|--------|-------------|
| Users VLAN (20) | Internet | ANY | ALLOW | Standard user internet access |
| Guest VLAN (60) | Internet | ANY | ALLOW | Guest internet access only |
| Users VLAN (20) | Management VLAN (30) | ANY | DENY | Prevent access to infrastructure management |
| Guest VLAN (60) | Users VLAN (20) | ANY | DENY | Prevent lateral movement from guest devices |
| Guest VLAN (60) | Management VLAN (30) | ANY | DENY | Block access to management interfaces |
| Any Internal VLAN | Any Internal VLAN | ANY | DENY | Default deny for inter-VLAN traffic |

Security model used in this lab follows the **least privilege principle** and a **default deny security posture**.

All traffic must be explicitly permitted by firewall policy.

---

# Security Controls Implemented

Network Segmentation  
VLAN architecture implemented on Cisco CBS250

Firewall Enforcement  
Traffic control using FortiGate NGFW policies

Guest Isolation  
Dedicated VLAN with internet-only access

Management Protection  
Separate MGMT VLAN with restricted access

Inter-VLAN Security  
Traffic filtered through firewall policies

Threat Modeling  
Documented attack surface and threats

Architecture Governance  
Architecture Decision Records (ADR)

Framework Alignment  
Zero Trust + CIS Controls

---

# Attack Surface Overview

Potential attack vectors and mitigations.

Internet Edge  
Threat: Port scanning  
Mitigation: Firewall policy enforcement

Guest Network  
Threat: Untrusted devices  
Mitigation: VLAN isolation

User Network  
Threat: Compromised endpoint  
Mitigation: Inter-VLAN firewall rules

Management Plane  
Threat: Unauthorized access  
Mitigation: MGMT VLAN isolation

Attack surface documentation:

https://pelen171004-wq.github.io/enterprise-security-lab/attack-surface.html

---

# Security Framework Alignment

Architecture decisions:

https://pelen171004-wq.github.io/enterprise-security-lab/architecture-decisions.html

Security frameworks referenced:

Zero Trust Network Architecture  
CIS Critical Security Controls

---

# Firewall Traffic Analysis

Firewall behaviour and segmentation were validated using FortiGate diagnostic tools.

Key troubleshooting techniques used in this lab include:

FortiGate debug flow  
Session table analysis  
Packet capture inspection  

These techniques allow verification of:

- firewall policy enforcement
- NAT translation
- traffic direction
- active session states

Example investigation confirmed that unauthorized traffic between security zones is correctly blocked by the firewall.

---

# Threat Model

Threat modeling identifies potential attack scenarios across network zones.

Documentation available in:

threat-model/THREAT-001-network-zones.md

---

# Troubleshooting & Operations

Operational troubleshooting includes:

- connectivity debugging
- firewall policy validation
- packet flow inspection
- network diagnostics

Troubleshooting playbook:

https://pelen171004-wq.github.io/enterprise-security-lab/troubleshooting.html

---

# Lab Roadmap

Future development phases.

Phase 1 – Core Network Security (Current)

FortiGate deployment  
Cisco switching  
VLAN segmentation  
Guest isolation  
Management network  
Firewall policy enforcement  

Phase 2 – Security Monitoring

SOC VLAN  
Log collection  
SIEM integration  
Traffic monitoring  

Phase 3 – Infrastructure Expansion

Server zone  
Backup infrastructure  
Security service segmentation  

Phase 4 – Enterprise Features

Firewall High Availability  
Configuration backup automation  
Security incident response playbooks  

---

# Architecture Decision Records

Architecture Decision Records document why design choices were made.

Examples include:

Network segmentation model  
Firewall policy architecture  
Management plane protection  

Documentation portal:

https://pelen171004-wq.github.io/enterprise-security-lab/architecture-decisions.html