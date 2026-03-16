# Diagram Standards

## Overview
This document defines diagram standards used in the Enterprise Security Lab documentation. Consistent diagram style improves readability, documentation quality, troubleshooting, and architecture understanding. These standards ensure that all diagrams across the project follow the same structure, naming conventions, and visual layout.

## Diagram Types
The following diagram types are used throughout this project.

### Architecture Diagram
Shows the high-level infrastructure architecture and trust boundaries. Typical components include Internet, Firewall, Switch, Access Point, Servers, and Monitoring systems. The purpose is to explain the overall architecture, demonstrate trust boundaries, and provide a quick understanding of the infrastructure.

### Physical Topology Diagram
Shows the physical connectivity between infrastructure devices. Typical information displayed includes device names, physical connections, trunk links, access ports, and infrastructure roles.

Example structure:

Internet  
|  
Firewall  
|  
Switch  
|      |      |  
AP    Server   Monitoring  

This diagram helps visualize the actual network layout and connectivity between devices.

### Logical Network Diagram
Shows logical segmentation of the network. Typical elements include VLAN IDs, subnets, security zones, and segmentation boundaries.

Example VLAN structure:

VLAN 10 – Management  
VLAN 20 – Users  
VLAN 30 – Servers  
VLAN 40 – Guest  
VLAN 50 – Monitoring  

The purpose of this diagram is to demonstrate segmentation, explain security design, and support firewall policy planning.

### Traffic Flow Diagram
Shows allowed and denied communication paths between network zones. It is used for firewall rule planning, security architecture explanation, and troubleshooting communication issues.

Example flows:

Users → Internet (Allow)  
Users → Servers (Allow)  
Guest → Internet (Allow)  
Guest → Internal Network (Deny)

### Monitoring / SOC Diagram
Shows how logs and monitoring data are collected across the environment. Typical elements include firewall logs, SNMP monitoring, syslog collectors, monitoring servers, and dashboards.

## Naming Conventions
Devices use consistent naming across all diagrams and documentation.

fw01 – firewall  
sw01 – switch  
ap01 – access point  
srv01 – server  
soc01 – monitoring system  

Avoid inconsistent naming such as Firewall1, MainSwitch, or Server-A.

## Visual Conventions
Recommended diagram layout:

Internet  
↓  
Firewall  
↓  
Switch  
↓  
AP / Servers / Monitoring  

## File Organization
Diagram source files are stored in the directory diagrams-src.

Exported diagrams are stored in the directory assets/images.

Recommended formats:

source diagrams: .drawio  
exported diagrams: .png or .svg

## Summary
Following these diagram standards ensures that diagrams remain clear, consistent, and easy to understand across the entire documentation project.