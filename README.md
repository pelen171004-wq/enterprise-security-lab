# Enterprise Security Lab

![Firewall](https://img.shields.io/badge/Firewall-FortiGate-red)
![Switch](https://img.shields.io/badge/Switch-Cisco_CBS250-blue)
![Architecture](https://img.shields.io/badge/Architecture-Segmented-green)
![Security](https://img.shields.io/badge/Security-Zero_Trust-orange)
![Project](https://img.shields.io/badge/Project-Enterprise_Lab-purple)

## Quick Navigation

- 🌐 **Live Lab Portal**  
  https://pelen171004-wq.github.io/enterprise-security-lab/

- 🏗 **Architecture Overview**  
  https://pelen171004-wq.github.io/enterprise-security-lab/architecture-overview.html

- 🔥 **FortiGate Documentation**  
  https://pelen171004-wq.github.io/enterprise-security-lab/device-fortigate.html

- 🔧 **Cisco CBS250 Documentation**  
  https://pelen171004-wq.github.io/enterprise-security-lab/device-cbs250.html

- 🛡 **Security Model**  
  https://pelen171004-wq.github.io/enterprise-security-lab/security-model.html

Live enterprise-style network security lab demonstrating VLAN segmentation, firewall enforcement, and security architecture design.

### Live Lab Portal
https://pelen171004-wq.github.io/enterprise-security-lab/

## Network Architecture

![Enterprise Security Lab Architecture](lab-architecture-v2.jpg)

### Technologies
FortiGate • Cisco CBS250 • VLAN Segmentation • Firewall Policies • Network Security Architecture

### Focus Areas
Network Security Engineering  
Infrastructure Security  
Security Architecture Design

### Key Features

- [x] VLAN-based network segmentation
- [x] FortiGate firewall policy enforcement
- [x] Guest network isolation
- [x] Management plane protection
- [x] Security framework alignment (Zero Trust / CIS)
- [x] Architecture decision records
- [x] Threat modeling

## Security Frameworks & Architecture Decisions

This lab also documents security design principles and architecture decisions.

### Security Frameworks
- [Zero Trust Networking Model](security-frameworks/zero-trust-model.md)
- [CIS Network Security Controls](security-frameworks/cis-network-controls.md)

### Architecture Decision Records
- [Network Segmentation Decision Record](security-frameworks/decision-record-segmentation.md)


### Additional Security Documentation
- [Threat Model](security-frameworks/threat-model.md)
- [Skills Mapping](skills-mapping.md)
- [Security Control Matrix](security-control-matrix.md)

### Lab Roadmap

Planned improvements for the Enterprise Security Lab.

#### Phase 1 – Core Network Security (current)

- FortiGate NGFW deployment
- Cisco CBS250 core switching
- VLAN segmentation
- Guest network isolation
- Management VLAN
- Inter-VLAN firewall policy model

#### Phase 2 – Security Monitoring

- SOC VLAN implementation
- Log collection
- SIEM integration
- Network traffic monitoring

#### Phase 3 – Infrastructure Expansion

- Server zone deployment
- Backup infrastructure zone
- Security service segmentation

#### Phase 4 – Enterprise Features

- Firewall High Availability (HA)
- Configuration backup automation
- Security incident response runbooks

## Architecture Decisions

Key architectural decisions are documented using ADR:

- Network segmentation model
- Firewall policy architecture
- Management plane protection

See:

architecture-decisions/

## Threat Model

- [Network Zone Threat Model](threat-model/THREAT-001-network-zones.md)