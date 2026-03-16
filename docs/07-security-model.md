# Security Model

## Overview

The security architecture of the Enterprise Security Lab is based on segmentation, least privilege access, and centralized policy enforcement through the firewall.

The objective is to reduce attack surface, prevent lateral movement, and improve monitoring visibility.

## Security Principles

The environment follows these principles:

- least privilege access
- default deny network communication
- role-based segmentation
- restricted administrative access
- centralized firewall enforcement
- monitoring and logging

## Trust Levels

Systems are grouped into different trust levels.

### Trusted Systems
Infrastructure components and management hosts.

Examples:

- firewall
- switches
- monitoring systems
- administrative workstations

### Internal Systems
Standard internal systems that provide services or run applications.

Examples:

- servers
- user workstations
- internal applications

### Untrusted Systems

Devices that cannot be fully trusted.

Examples:

- guest devices
- unknown wireless clients
- unmanaged endpoints

## Segmentation Strategy

Network segmentation is implemented using VLANs and firewall-controlled routing.

The segmentation provides:

- isolation of management traffic
- protection of server infrastructure
- containment of guest devices
- controlled communication between zones

## Administrative Security

Administrative access must follow strict controls:

- only allowed from the management VLAN
- restricted to secure protocols
- limited to authorized administrators
- logged where possible

## Guest Security Model

Guest networks are treated as untrusted.

The guest network policy is:

- allow outbound internet access
- deny access to internal networks
- deny access to management interfaces
- isolate from internal services

## Monitoring and Visibility

Monitoring and logging are critical parts of the security model.

Relevant visibility areas include:

- firewall logs
- denied traffic attempts
- authentication events
- device health monitoring
- unusual network activity

## Security Goals

The security architecture aims to reduce:

- unauthorized administrative access
- lateral movement across the network
- exposure of internal services
- uncontrolled access between network segments

## Summary

The security model combines segmentation, centralized firewall control, and monitoring visibility to provide a practical enterprise-style security architecture.