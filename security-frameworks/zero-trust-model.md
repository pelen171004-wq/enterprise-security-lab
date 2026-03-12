# Zero Trust Networking Model

This lab architecture follows core Zero Trust networking principles.

Zero Trust assumes that no network zone should be trusted by default.
All communication between zones must be explicitly allowed.

---

## Principles implemented in this lab

• No implicit trust between network segments  
• Explicit firewall policies controlling traffic  
• Segmentation between user, management and guest networks  
• Isolation of guest devices from internal infrastructure  

---

## Network zones

MGMT   = management plane  
USERS  = workstation network  
GUEST  = internet-only network  
SOC    = monitoring and logging zone (planned)  
SERVERS = internal services (planned)  
BACKUP = backup infrastructure (planned)

---

## Implementation

Segmentation implemented using:

• FortiGate firewall VLAN interfaces  
• Firewall policy rules  
• Cisco CBS250 VLAN switching  

Example traffic model:
