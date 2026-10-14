# Cisco Networking Labs

> **Hands-on networking practice using Cisco Packet Tracer**

This repository documents networking practicals completed while learning network configuration, troubleshooting and routing. Each practical is organized with an overview, objective, procedure, verification commands, screenshots or media where available, a file guide and a **What We Learned** section.

## Repository Overview

| Practical | Topics covered | Main files |
|---|---|---|
| [01 — IP Configuration](./01-IP-CONFIGURATION/README.md) | IPv4 addressing, interfaces, routing table and ping | [Practical report](./01-IP-CONFIGURATION/01-IP-CONFIGURATION-PRACTICAL/01-IP-CONFIGURATION.md) · [Packet Tracer file](./01-IP-CONFIGURATION/01-IP-CONFIGURATION-PRACTICAL/practical1.pkt) |
| [02 — DHCP Configuration](./02%20DHCP%20AND%20ROUTING/DHCP%20PRACTICAL%20FILES/README.md) | Automatic IP configuration, DHCP pool and client verification | [DHCP project](./02%20DHCP%20AND%20ROUTING/DHCP%20PRACTICAL%20FILES/dhcp.pkt) · [Video](./02%20DHCP%20AND%20ROUTING/DHCP%20PRACTICAL%20FILES/Screen%20Recording%202026-09-30%20202440.mp4) |
| [03 — RIP v2 Simulation](./03-RIP-v2-Simulation/README.md) | Dynamic routing, ARP, ICMP, route learning and Simulation Mode | [Packet Tracer file](./03-RIP-v2-Simulation/Ripconfiguration.pkt) |
| [04 — Static Routing](./STATIC%20ROUTING/STATIC%20ROUTING%20PRACTICAL/README.md) | Static routes, destination networks, next hops and route verification | [Practical video](./STATIC%20ROUTING/STATIC%20ROUTING%20PRACTICAL/Screen%20Recording%202026-10-03%20171408.mp4) |

## How to Use This Repository

1. Open the README for the practical you want to review.
2. Read the objective and network overview before opening the lab.
3. Download or open the relevant `.pkt` file in Cisco Packet Tracer.
4. Follow the procedure and run the verification commands.
5. Compare your output with the screenshots and notes provided.
6. Review the **What We Learned** and **Result** sections.

## Common Verification Commands

```text
show ip interface brief
show ip route
show ip protocols
ping <destination-ip>
ipconfig
```

Use only the commands relevant to the practical and the device where you are running them. For example, Cisco IOS commands belong in the router CLI, while `ipconfig` and ping are commonly run from a PC command prompt.

## Learning Goals

- Understand IPv4 addressing, subnet masks and default gateways.
- Connect routers, switches and PCs in Packet Tracer.
- Verify interface status and routing tables.
- Configure and understand DHCP, static routing and RIP v2.
- Use ping and Simulation Mode to investigate connectivity.
- Record practical work in clear, reproducible documentation.

## Notes

- A `.pkt` file requires Cisco Packet Tracer to open and inspect.
- Video and screenshot links work only when the referenced file exists at the linked repository path.
- Results are documented from the practical evidence available; any test marked as pending should be completed and its output added before reporting it as successful.

## Author

**Kartik Pottabathini**  
GitHub: [@kartik-71](https://github.com/kartik-71)
