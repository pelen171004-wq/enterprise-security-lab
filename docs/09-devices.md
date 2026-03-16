# Device Inventory

## Overview

This document lists the infrastructure devices used in the Enterprise Security Lab.

Maintaining an accurate device inventory helps with:

- documentation clarity
- troubleshooting
- configuration management
- security planning

## Naming Convention

Devices follow a consistent naming model.

Examples:

- fw01 – firewall
- sw01 – switch
- ap01 – access point
- srv01 – server
- soc01 – monitoring system

## Device Inventory

| Hostname | Role | Model | Management IP | VLAN |
|---|---|---|---|---|
| fw01 | Firewall | FortiGate 60E | 10.10.10.10 | 10 |
| sw01 | Managed Switch | Cisco CBS250 | 10.10.10.11 | 10 |
| ap01 | Wireless Access Point | Enterprise AP | 10.10.10.20 | 10 |
| srv01 | Infrastructure Server | Linux / Windows Server | 10.10.30.10 | 30 |
| soc01 | Monitoring System | Monitoring Platform | 10.10.50.10 | 50 |

## Device Roles

### fw01 – Firewall

The firewall provides:

- network segmentation
- inter-VLAN routing
- security policy enforcement
- NAT for outbound traffic
- logging and monitoring

### sw01 – Managed Switch

The switch provides:

- VLAN segmentation
- endpoint connectivity
- trunk links to firewall
- access ports for devices

### ap01 – Access Point

The wireless access point provides:

- corporate wireless access
- guest wireless access
- VLAN mapping for SSIDs

### srv01 – Infrastructure Server

Servers host internal services such as:

- DNS
- DHCP
- application services
- directory services

### soc01 – Monitoring System

Monitoring systems collect logs and telemetry from network devices.

Possible functions include:

- syslog collection
- SNMP monitoring
- dashboards
- security analysis

## Management Network

Infrastructure devices should be managed through the management VLAN.

Recommended practices:

- restrict admin access
- use secure protocols
- document management IP addresses
- track configuration changes

## Summary

The device inventory provides a structured view of the infrastructure components used in the lab and supports operational documentation and troubleshooting.