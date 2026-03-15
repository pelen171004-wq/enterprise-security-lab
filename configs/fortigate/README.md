# FortiGate Configuration Notes

Device name: FG

Role:
- Inter-VLAN routing
- Firewall policy enforcement
- NAT to WAN
- DHCP services
- Management plane protection

Current VLAN interfaces:
- VLAN20 – 10.10.20.1/24
- VLAN30 – 10.10.30.1/24
- VLAN60 – 10.10.60.1/24

Current policy model:
- USERS → WAN = ALLOW
- GUEST → WAN = ALLOW
- USERS → MGMT = DENY
- GUEST → USERS = DENY
- GUEST → MGMT = DENY
- DEFAULT INTERNAL = DENY
