# Cisco CBS250 (SWA)

## Device Role

The Cisco CBS250 switch acts as the Layer2 core switch in the Enterprise Security Lab.

Its primary role is to provide VLAN segmentation and connect internal networks to the FortiGate firewall, which performs routing and security enforcement.

---

## Device Information

Device: Cisco CBS250  
Hostname: SWA  

Management IP:

10.10.30.2

Management VLAN:

VLAN30

Default Gateway:

10.10.30.1 (FortiGate)

---

## Network Role

The switch provides Layer2 switching for the following VLANs:

| VLAN | Name | Purpose |
|-----|-----|------|
| VLAN20 | USERS | Client network |
| VLAN30 | MGMT | Management access |
| VLAN60 | GUEST | Guest internet access |

All inter-VLAN traffic is routed and filtered by the FortiGate firewall.

---

## Port Roles

| Port | Role |
|----|----|
| Gi1 | Trunk connection to FortiGate |
| Gi2 | Fallback / break-glass management |
| Gi3 | Administrative access |
| Gi4 | Guest VLAN access |
| Gi5 | Users VLAN access |

---

## Security Design

Security architecture principles applied:

• VLAN network segmentation  
• Dedicated management VLAN  
• Guest network isolation  
• Firewall-enforced inter-VLAN communication  

The switch does not perform Layer3 routing or firewall inspection.

---

## Configuration Snapshot

The current configuration snapshot is stored here:

`swa-config.txt`
