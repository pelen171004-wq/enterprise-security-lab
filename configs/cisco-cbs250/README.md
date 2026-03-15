# Cisco CBS250 Configuration Notes

Device name: SWA

Role:
- Layer 2 switching
- VLAN segmentation
- Access / trunk switching
- Management access in VLAN30

Management IP:
- 10.10.30.2/24
- Default gateway: 10.10.30.1

Port roles:
- Gi1 = trunk to FortiGate
- Gi2 = break-glass / fallback management
- Gi3 = management/admin access
- Gi4 = guest VLAN60
- Gi5 = users VLAN20