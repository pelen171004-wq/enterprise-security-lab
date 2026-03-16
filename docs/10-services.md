# Services

## Overview

This document describes the internal services running in the Enterprise Security Lab environment.

Documenting services helps with:

- architecture clarity
- troubleshooting
- dependency tracking
- operational visibility

## Core Infrastructure Services

The lab may include several internal services that support network functionality.

| Service | Host | Purpose |
|---|---|---|
| DNS | srv01 | Name resolution |
| DHCP | srv01 | Dynamic IP allocation |
| NTP | Infrastructure | Time synchronization |
| Monitoring | soc01 | Network monitoring and logging |
| Application services | srv01 | Internal applications |

## DNS

The DNS service provides hostname resolution for internal systems.

Functions include:

- resolving internal hostnames
- forwarding queries to external resolvers
- supporting application connectivity

## DHCP

DHCP automatically assigns IP addresses to client devices.

DHCP scope example:

| VLAN | Subnet | Gateway |
|---|---|---|
| Users | 10.10.20.0/24 | 10.10.20.1 |
| Guest | 10.10.40.0/24 | 10.10.40.1 |

Infrastructure devices typically use static addressing.

## Monitoring

Monitoring services provide operational visibility.

Typical monitoring data includes:

- device status
- CPU and memory usage
- network traffic
- service availability
- log events

Monitoring may use:

- SNMP
- syslog
- API integrations

## Application Services

Application services may run on internal servers.

Examples include:

- web applications
- file services
- development or test platforms

Access to application services should be controlled by firewall policies.

## Service Dependencies

Some services depend on others to function correctly.

Example dependencies:

| Service | Depends On |
|---|---|
| Applications | DNS |
| Monitoring | Network connectivity |
| DHCP clients | DHCP server |

Understanding dependencies helps during troubleshooting.

## Summary

Documenting services ensures that administrators understand which systems provide critical functionality and how those services interact.