# SIMULATION — Network Segmentation & Security Review

**Date:** September 15, 2026  
**Role:** Junior Network Security Analyst — Co-op *(Simulation)*  
**Environment:** Southwestern Ontario Technology & Security Services (SOTS) *(Fictional)*  
**Assessment Type:** Network Security / Segmentation Review

> **SIMULATION NOTICE:** This is a fictional cybersecurity career exercise. All organizations, systems, networks, IP addresses, and assessment data are fictional.

---

## Assessment Overview

A network-security review was conducted to evaluate segmentation and access controls between the Staff, Server, Management, and Internet-facing environments.

The primary issue identified was an overly permissive rule allowing unrestricted traffic from the Staff VLAN to the Server VLAN.

### Current Design

```text
Staff VLAN
10.10.20.0/24
      |
      | ALLOW ALL / ANY PORT
      ↓
Server VLAN
10.10.30.0/24
