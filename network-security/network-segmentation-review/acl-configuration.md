# SIMULATION — Staff VLAN ACL Configuration

> This configuration was created and tested in a fictional Cisco Packet Tracer environment for a cybersecurity career simulation.

## ACL Purpose

The `STAFF-FILTER` extended ACL was designed to apply least-privilege network access to the Staff VLAN.

The policy allows required business services while restricting unnecessary access to critical infrastructure.

## ACL Configuration

```text
ip access-list extended STAFF-FILTER

permit tcp 10.10.20.0 0.0.0.255 host 10.10.30.10 eq 443

permit udp 10.10.20.0 0.0.0.255 host 10.10.40.10 eq 53
permit tcp 10.10.20.0 0.0.0.255 host 10.10.40.10 eq 53

permit udp 10.10.20.0 0.0.0.255 host 10.10.40.10 eq 88
permit tcp 10.10.20.0 0.0.0.255 host 10.10.40.10 eq 88

deny ip 10.10.20.0 0.0.0.255 10.10.50.0 0.0.0.255

deny ip 10.10.20.0 0.0.0.255 10.10.10.0 0.0.0.255

deny ip 10.10.20.0 0.0.0.255 any
