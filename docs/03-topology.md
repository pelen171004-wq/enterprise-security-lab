# Topology

## Overview

The topology is designed to reflect a small enterprise network with a perimeter firewall, managed switching, wireless access, internal services, and multiple segmented VLANs.

The environment is structured to demonstrate clear trust boundaries, service placement, and controlled traffic flows.

## Physical Topology

At a high level, the environment consists of:

- internet uplink
- perimeter firewall
- managed switch infrastructure
- wireless access point
- internal servers and services
- management and monitoring systems

A simplified representation:

```text
Internet
   |
[ Firewall ]
   |
[ Core / Access Switch ]
 |       |        |        |
AP     Servers   Admin    Monitoring