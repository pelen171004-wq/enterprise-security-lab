# Threat Model

This document describes the main security threats considered in the Enterprise Security Lab design.

---

## 1. Management plane exposure

### Threat
Administrative interfaces exposed to untrusted networks.

### Risk
Attackers or infected endpoints could attempt access to firewall or switch management interfaces.

### Mitigations implemented
- Dedicated management VLAN (VLAN30)
- Trusted host restriction on FortiGate admin account
- Local-in deny for Guest VLAN
- Break-glass access separated from normal user access

---

## 2. Lateral movement between user and management networks

### Threat
A compromised user endpoint attempts to reach management systems.

### Risk
Privilege escalation, device compromise, broader infrastructure impact.

### Mitigations implemented / planned
- VLAN separation
- FortiGate inter-zone enforcement
- USERS → MGMT deny policy
- Least privilege traffic model

---

## 3. Guest network abuse

### Threat
Guest devices attempt to access internal systems.

### Risk
Internal reconnaissance, unauthorized access attempts, malware spread.

### Mitigations implemented
- Guest VLAN isolated from internal networks
- Guest allowed to internet only
- Guest blocked from FortiGate management plane

---

## 4. Weak observability

### Threat
Security events occur without sufficient visibility.

### Risk
Delayed detection, poor troubleshooting, incomplete incident understanding.

### Planned mitigations
- Monitoring VLAN (SOC)
- Traffic logging
- Session troubleshooting workflow
- Debug flow runbooks
- Central logging

---

## 5. Overly broad trust between zones

### Threat
Too much implicit trust between network segments.

### Risk
Large blast radius after a compromise.

### Mitigations implemented / planned
- Zone-based segmentation
- Explicit firewall policy model
- Default-deny mindset
- Restricted service flows between zones

---

## Security objective

The lab is designed to reduce attack surface, limit lateral movement, isolate risk, and improve operational troubleshooting visibility.
