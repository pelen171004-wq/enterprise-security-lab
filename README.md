# Enterprise Security Lab

## Overview

This repository contains the technical documentation and supporting artifacts for an enterprise-style network security lab.

The lab is designed to demonstrate segmented network architecture, firewall-enforced inter-VLAN control, management plane protection, wireless isolation, troubleshooting methodology, and SOC-oriented visibility.

## Objectives

This project was built to model a practical small-to-medium enterprise security environment with clear design logic and operational structure.

Key goals:

- implement secure network segmentation
- enforce inter-zone traffic control through the firewall
- protect management infrastructure
- document architecture decisions and trade-offs
- simulate operational and security monitoring use cases

## Environment Scope

The lab includes:

- FortiGate firewall
- Cisco CBS250 switching
- VLAN-based segmentation
- management, user, guest, server, backup, and SOC-oriented zones
- enterprise-style technical documentation
- security visualization and troubleshooting workflows

## Documentation Areas

Detailed documentation is organized around the following topics:

- topology
- network zones
- architecture overview
- architecture decisions
- security model
- firewall policy behavior
- security operations
- troubleshooting
- device documentation

## Project Structure

docs/           technical documentation  
configs/        selected configuration snippets  
diagrams-src/   editable source diagrams  
assets/images/  exported diagrams and visuals

## Design Principles

The environment follows these principles:

- least privilege
- default deny between zones unless explicitly allowed
- dedicated management access
- centralized policy enforcement
- visibility-first operational thinking

## Intended Audience

This project is intended as a portfolio and technical documentation artifact for roles such as:

- Network Engineer
- Network Security Engineer
- Senior Infrastructure Engineer
- Network Architect
- SOC / Blue Team oriented infrastructure roles

## Status

The lab is operational and the documentation is continuously refined to better reflect enterprise documentation standards.