# Enterprise Security Lab

Live enterprise-style network security lab demonstrating VLAN segmentation, firewall enforcement, and security architecture design.

### Live Lab Portal
https://pelen171004-wq.github.io/enterprise-security-lab/

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

# enterprise-security-lab
architecture/Enterprise_Lab
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