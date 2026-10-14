# Cisco Networking Labs

> **Hands-on networking practice using Cisco Packet Tracer**

This repository documents networking practicals completed while learning network configuration, troubleshooting and routing. Each practical includes its objective, procedure, configuration or verification details, screenshots where available, and a **What I Learned** section.

## Repository Overview

| Practical | Topics covered | Main files |
|---|---|---|
| [01 — IP Configuration](./01-IP-CONFIGURATION/README.md) | IPv4 addressing, interfaces, routing table and ping | [Practical report](./01-IP-CONFIGURATION/01-IP-CONFIGURATION-PRACTICAL/01-IP-CONFIGURATION.md) · [Packet Tracer file](./01-IP-CONFIGURATION/01-IP-CONFIGURATION-PRACTICAL/practical1.pkt) |
| [02 — DHCP Configuration](./02%20DHCP%20AND%20ROUTING/DHCP%20PRACTICAL%20FILES/README.md) | Automatic IP configuration, DHCP pool and client verification | [DHCP project](./02%20DHCP%20AND%20ROUTING/DHCP%20PRACTICAL%20FILES/dhcp.pkt) |
| [03 — RIP v2 Simulation](./03-RIP-v2-Simulation/README.md) | Dynamic routing, ARP, ICMP, route learning and Simulation Mode | [Packet Tracer file](./03-RIP-v2-Simulation/Ripconfiguration.pkt) |
| [04 — Static Routing](./04%20static%20routing/) | Static routes, destination networks, next hops and route verification | [Practical README](./04%20static%20routing/STATIC%20ROUTING%20PRACTICAL/README.md) |
| [05 — STP (Spanning Tree Protocol)](./05%20Stp/README.md) | Root bridge election, redundant switch links, loop prevention and ping verification | [Ping results](./05%20Stp/STP-Ping-Results.svg) |
| [06 — OSPF Three-Router Lab](./06%20OSPF/README.md) | OSPFv2, area 0, neighbor adjacencies, dynamic routes and end-to-end ping | [Screenshot evidence PDF](./06%20OSPF/OSPF_Screenshots.pdf) |

## How to Use This Repository

1. Open the README for the practical you want to review.
2. Read the objective and network overview.
3. Follow the configuration and verification steps.
4. Compare the observed output with the screenshots.
5. Review the **What I Learned** and **Result** sections.

## Common Verification Commands

```text
show ip interface brief
show ip route
show ip protocols
show ip ospf neighbor
ping <destination-ip>
ipconfig
```

Use commands in the correct device CLI. Cisco IOS commands belong in router or switch CLI; `ipconfig` and PC ping tests are run from a PC command prompt.

## Learning Goals

- Understand IPv4 addressing, subnet masks and default gateways.
- Connect routers, switches and PCs in Packet Tracer.
- Verify interface status and routing tables.
- Configure and understand DHCP, static routing, RIP v2, STP and OSPF.
- Use ping and simulation tools to investigate connectivity.
- Document practical work in clear, reproducible steps.

## Author

**Kartik Pottabathini**  
GitHub: [@kartik-71](https://github.com/kartik-71)
