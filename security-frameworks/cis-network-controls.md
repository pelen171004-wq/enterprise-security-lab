# CIS Network Security Controls

This lab environment follows selected principles from the CIS Critical Security Controls related to network security.

Reference: Center for Internet Security (CIS)

---

## Control 4 – Secure Configuration of Network Devices

Network devices are configured according to security best practices.

Implemented:

• Dedicated management VLAN (VLAN30)  
• Restricted management access  
• Break-glass port on CBS250 switch  
• Segmented VLAN architecture

Devices covered:

• FortiGate 60E  
• Cisco CBS250 switch

---

## Control 12 – Network Infrastructure Management

The lab includes monitoring-ready architecture.

Planned components:

• SOC monitoring VLAN (VLAN40)  
• Central logging  
• Security monitoring stack

Future integration:

• SIEM
• Log analysis
• Security event correlation

---

## Control 13 – Network Monitoring and Defense

Traffic control and inspection are enforced through firewall segmentation.

Security enforcement:

• Inter-VLAN firewall policies  
• Guest network isolation  
• Controlled access between network zones  

Example policy model:

MGMT → ALL = restricted admin access
USERS → WAN = allowed
GUEST → INTERNAL = blocked
SERVERS → USERS = controlled services

---

## Security Objective

Improve network visibility, segmentation and threat containment using layered security controls.