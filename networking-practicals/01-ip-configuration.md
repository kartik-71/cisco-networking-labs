# Practical 1 – IP Address Configuration

## Practical Name
**Basic IPv4 Address Configuration and Network Connectivity**

## Objective
To understand and configure IPv4 addresses on PCs and router interfaces in Cisco Packet Tracer and verify basic network connectivity.

## Network Details

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| PC0 | FastEthernet | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | FastEthernet | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| PC2 | FastEthernet | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |
| Router A | Fa0/0 | 192.168.1.1 | 255.255.255.0 | — |
| Router A | S0/1/0 | 10.0.0.1 | 255.255.255.252 | — |
| Router B | S0/1/0 | 10.0.0.2 | 255.255.255.252 | — |
| Router B | Fa0/0 | 192.168.2.1 | 255.255.255.0 | — |
| PC3 | FastEthernet | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC4 | FastEthernet | 192.168.2.11 | 255.255.255.0 | 192.168.2.1 |
| PC5 | FastEthernet | 192.168.2.12 | 255.255.255.0 | 192.168.2.1 |

## Networks Used
- LAN 1: **192.168.1.0/24**
- Router-to-router serial link: **10.0.0.0/30**
- LAN 2: **192.168.2.0/24**

## Basic Verification Commands

```text
show ip interface brief
show ip route
ping 10.0.0.2
ping 192.168.2.10
```

## What We Learn
- IPv4 addressing and subnet masks
- Default gateway configuration
- Router interface addressing
- Serial point-to-point addressing
- Checking interface status with `show ip interface brief`
- Viewing connected networks with `show ip route`
- Testing connectivity using `ping`

## Tools Used
- Cisco Packet Tracer
- Cisco routers and switches
- PCs
- IPv4 addressing
