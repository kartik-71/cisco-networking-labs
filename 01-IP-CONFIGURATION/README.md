# 01 — IP Configuration Practical

> **Cisco Packet Tracer · IPv4 addressing · Interface verification · Ping testing**

## Overview

This folder documents an introductory networking practical in Cisco Packet Tracer. The lab contains two routers, two switches and six PCs. It focuses on connecting network devices, assigning IPv4 addresses, checking interface status and testing communication between PCs.

## Practical Details

| Item | Details |
|---|---|
| Practical name | IP Configuration and Basic Network Connectivity |
| Software | Cisco Packet Tracer |
| Devices | 2 routers, 2 switches and 6 PCs |
| Main topics | IPv4 addressing, subnet masks, default gateways, interfaces, routing tables and ICMP ping |
| Evidence | Packet Tracer project, screenshots and screen recording |

## Practical Objectives

- Build a small network using routers, switches and PCs.
- Configure IP addresses and default gateways on the required devices.
- Check router interface status and addressing.
- Inspect the routing table.
- Use ping to test connectivity between PCs.
- Record the practical in a format that can be reviewed and repeated.

## Practical Report

Open the detailed [IP Configuration Practical](./01-IP-CONFIGURATION-PRACTICAL/01-IP-CONFIGURATION.md) for the procedure, verification commands, screenshots, video and learning outcomes.

## Files and Media

| File | Purpose |
|---|---|
| [Detailed practical report](./01-IP-CONFIGURATION-PRACTICAL/01-IP-CONFIGURATION.md) | Procedure, results, screenshots and learning outcomes |
| [Packet Tracer project](./01-IP-CONFIGURATION-PRACTICAL/practical1.pkt) | Opens the network topology in Cisco Packet Tracer |
| [Screen recording](./01-IP-CONFIGURATION-PRACTICAL/media/Screen%20Recording%202026-09-08%20202717.mp4) | Video demonstration of the practical |
| [Interface status screenshot](./01-IP-CONFIGURATION-PRACTICAL/media/01-show-ip-interface-brief.svg) | Illustrates the `show ip interface brief` output |
| [Ping screenshot](./01-IP-CONFIGURATION-PRACTICAL/media/02-ping-pc0-to-pc1.svg) | Illustrates PC-to-PC connectivity testing |
| [Routing table screenshot](./01-IP-CONFIGURATION-PRACTICAL/media/03-show-ip-route.svg) | Illustrates the `show ip route` output |
| [Additional interface screenshot](./01-IP-CONFIGURATION-PRACTICAL/media/04-show-ip-interface-brief-duplicate.svg) | Additional interface-status illustration |

## Main Commands

```text
show ip interface brief
show ip route
ping <destination-ip>
```

## What We Learned

This practical introduced the basic workflow of building a network in Packet Tracer, connecting routers and switches, assigning IP addresses, and checking whether interfaces are active. It also provided practice reading a routing table and using ping to check whether two devices can communicate.

## Result

The practical files and supporting media are organized for review. Open the Packet Tracer project to inspect the topology, and use the detailed report to follow the procedure and understand the purpose of each piece of evidence.
