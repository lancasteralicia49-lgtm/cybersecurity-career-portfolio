# SIMULATION — Network Segmentation Lab Validation

**Date:** September 15, 2026  
**Lab:** Cisco Packet Tracer  
**Assessment:** Network Segmentation & ACL Validation

> **SIMULATION NOTICE:** This is a fictional cybersecurity career exercise. The network, systems, IP addresses, and test results are part of a simulated environment.

## Lab Objective

Validate that Staff VLAN access is restricted according to the least-privilege network security policy.

The lab was built in Cisco Packet Tracer using:

- Cisco 2911 router
- Cisco 2960 switch
- Staff PC
- Application Server
- Domain Server
- Backup Server
- Management PC

## VLANs

| VLAN | Purpose | Network | Gateway |
|---:|---|---|---|
| 10 | Management | 10.10.10.0/24 | 10.10.10.1 |
| 20 | Staff | 10.10.20.0/24 | 10.10.20.1 |
| 30 | Application | 10.10.30.0/24 | 10.10.30.1 |
| 40 | Domain | 10.10.40.0/24 | 10.10.40.1 |
| 50 | Backup | 10.10.50.0/24 | 10.10.50.1 |

## Baseline — Before ACL

Before the ACL was applied, the Staff PC could reach:

- Application Server
- Domain Server
- Backup Server
- Management PC

This demonstrated that the initial routing configuration allowed unrestricted inter-VLAN connectivity.

## Security Control

An extended ACL named `STAFF-FILTER` was applied inbound to:

```text
GigabitEthernet0/0.20
