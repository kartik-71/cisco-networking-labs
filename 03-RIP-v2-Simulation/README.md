# Simulation of ARP, ICMP and RIP v2 Routing

> **Networking Practical · Cisco Packet Tracer · Dynamic routing · Packet simulation**

## 1. Practical Overview

This practical uses a three-router network to study how end devices communicate across multiple IP networks. The topology contains routers R0, R1 and R2, three switches and six PCs. Each router connects to a local LAN, and serial links connect R0 to R1 and R1 to R2.

The practical focuses on **RIP version 2 (RIP v2)** for dynamic route exchange, **ARP** for resolving a local next-hop IPv4 address to a MAC address, and **ICMP** for connectivity testing. Router command output and PC ping results help verify interface status, routing information and network reachability.

## 2. Practical Details

| Item | Details |
|---|---|
| Practical name | Simulation of ARP, ICMP and Routing Process Using Cisco Packet Tracer |
| Software | Cisco Packet Tracer |
| Devices | 3 routers, 3 switches and 6 PCs |
| Routing protocol | RIP version 2 |
| Connections | Ethernet LAN links and serial router-to-router links |
| Main concepts | IPv4 addressing, routing tables, RIP v2, ARP, ICMP and Simulation Mode |
| Verification | `show ip interface brief`, `show ip route`, `show ip protocols` and ping |

## 3. Objective

To configure and verify a multi-router network, inspect RIP v2 route learning, test connectivity between router LAN interfaces, and observe ARP/ICMP packet events in Cisco Packet Tracer Simulation Mode.

## 4. Topology Overview

- **R0** connects to the first LAN, `192.168.1.0/24`.
- **R1** connects to the middle LAN, `192.168.2.0/24`.
- **R2** connects to the third LAN, `192.168.3.0/24`.
- The R0–R1 serial network is `10.0.0.0/30`.
- The R1–R2 serial network is `10.0.0.4/30`.
- RIP v2 advertises the relevant networks so routers can learn routes to networks that are not directly connected.

![Three-router RIP v2 topology](https://github.com/user-attachments/assets/5f083d99-e642-49ba-9808-38153150785c)

Open [Ripconfiguration.pkt](./Ripconfiguration.pkt) in Cisco Packet Tracer to inspect the saved topology and configuration.

## 5. Router Addressing Summary

| Router | LAN interface address used in tests | Serial link information shown in evidence |
|---|---|---|
| R0 | `192.168.1.1` | `10.0.0.1` on the R0–R1 link |
| R1 | `192.168.2.1` | `10.0.0.2` toward R0 and `10.0.0.5` toward R2 |
| R2 | `192.168.3.1` | The R1–R2 link uses `10.0.0.4/30` |

The LANs use a `/24` mask (`255.255.255.0`) and the serial links use `/30` masks (`255.255.255.252`). Confirm these values against the saved Packet Tracer project if you change the addressing plan.

## 6. Practical Files and Video Status

**Packet Tracer project:** [Open/download Ripconfiguration.pkt](./Ripconfiguration.pkt)

**Video:** The README is ready for a video link, but a demonstration MP4 is not currently present inside `03-RIP-v2-Simulation/` in the repository. Upload the recording to this folder (or a `media/` subfolder) and update this section with its exact filename to make the link work.

## 7. R0 — Verification Evidence

### 7.1 Network topology

![R0 network topology](https://github.com/user-attachments/assets/f3f0338a-6476-4539-be27-b6daf06a07f9)

This screenshot shows R0 connected to its local switch and the serial link toward R1.

### 7.2 `show ip interface brief`

![R0 show ip interface brief](https://github.com/user-attachments/assets/66300f19-c31b-4758-aa2d-67ddc4736a2b)

**Purpose:** checks interface names, assigned IP addresses and operational status.

The captured output shows FastEthernet0/0 at `192.168.1.1` and Serial0/1/0 at `10.0.0.1`, both **up/up**. Other listed interfaces are administratively down in this capture.

### 7.3 `show ip route`

![R0 show ip route](https://github.com/user-attachments/assets/aeb0ee86-6d13-4a31-9009-81d2a14fc5ec)

**Purpose:** displays the routes R0 can use to forward traffic. The output includes directly connected routes marked `C` and RIP-learned routes marked `R`, showing that R0 has learned remote network information.

### 7.4 `show ip protocols`

![R0 show ip protocols](https://github.com/user-attachments/assets/b47eb815-2b59-4387-85a1-8542a0c809e5)

**Purpose:** verifies the routing protocol, RIP version and advertised networks. The captured output identifies RIP and indicates version 2 for sending and receiving updates. The listed networks include `10.0.0.0` and `192.168.1.0`.

## 8. R1 — Verification Evidence

The following screenshots were supplied for R1. Upload them to this practical's `media/` folder with the filenames shown here for the embedded image links to display.

### 8.1 `show ip interface brief`

![R1 show ip interface brief](./media/05-r1-show-ip-interface-brief.png)

The supplied output shows FastEthernet0/0 at `192.168.2.1`, Serial0/1/0 at `10.0.0.2`, and Serial0/1/1 at `10.0.0.5`; all three are **up/up** in the screenshot.

### 8.2 `show ip route`

![R1 show ip route](./media/06-r1-show-ip-route.png)

The routing table shows directly connected networks and remote routes learned through RIP. Entries marked `R` are RIP-learned routes; their next-hop addresses and outgoing interfaces help explain how packets are forwarded.

### 8.3 `show ip protocols`

![R1 show ip protocols](./media/07-r1-show-ip-protocols.png)

The supplied output indicates RIP v2 send/receive behaviour. The networks listed include `10.0.0.0` and `192.168.2.0`, with routing information sources `10.0.0.1` and `10.0.0.6`.

## 9. PC0 Connectivity Tests

Ping uses ICMP Echo Request and Echo Reply messages to test reachability.

### 9.1 PC0 to R0

```text
ping 192.168.1.1
```

![PC0 ping to R0](./media/08-pc0-ping-r0.png)

**Captured result:** 4 packets sent, 4 received, 0% packet loss.

### 9.2 PC0 to R1

```text
ping 192.168.2.1
```

![PC0 ping to R1](./media/09-pc0-ping-r1.png)

**Captured result:** 4 packets sent, 4 received, 0% packet loss.

### 9.3 PC0 to R2

```text
ping 192.168.3.1
```

![PC0 ping to R2](./media/10-pc0-ping-r2.png)

**Evidence still required:** capture and upload the output of this test before reporting its result.

## 10. Procedure

1. Open Cisco Packet Tracer and open the saved project or create the three-router topology.
2. Place three routers, three switches and six PCs.
3. Connect two PCs to each switch and connect each switch to its local router.
4. Connect R0 to R1 and R1 to R2 with serial links.
5. Assign the IPv4 addresses and subnet masks to router interfaces and PCs.
6. Configure the default gateway on each PC to point to its local router interface.
7. Enable the required router interfaces.
8. Configure RIP version 2 on each router and advertise the LAN and serial networks used in the topology.
9. Run `show ip interface brief` on the routers to verify interface addresses and status.
10. Run `show ip protocols` to check the RIP version and configured networks.
11. Run `show ip route` to confirm that remote routes have been learned.
12. From PC0, run the ping tests to `192.168.1.1`, `192.168.2.1` and `192.168.3.1`.
13. Switch to **Simulation** mode and enable the relevant ARP and ICMP event filters.
14. Create a Simple PDU between a source and destination PC.
15. Use **Capture / Forward** to step through events and open packet details to inspect what happens at each hop.
16. Save the project and capture evidence of the topology, router command outputs, ping results and simulation events.

## 11. Main Concepts

### ARP — Address Resolution Protocol

ARP helps a device resolve an IPv4 next-hop address to a MAC address on the local network. The sender needs the destination's MAC address—or the MAC address of its next hop—before it can send an Ethernet frame.

### ICMP — Internet Control Message Protocol

ICMP is used for network diagnostics and error reporting. Ping sends ICMP Echo Requests and waits for Echo Replies. Successful replies indicate that the destination responded to the test.

### RIP v2 — Dynamic routing

RIP v2 allows neighbouring routers to exchange route information dynamically. It uses hop count as its metric. The `show ip route` command helps identify routes learned through RIP, while `show ip protocols` displays routing-protocol settings.

## 12. File Guide

| File | Main purpose |
|---|---|
| [`README.md`](./README.md) | Main report with overview, topology, procedure, evidence and learning outcomes |
| [`Ripconfiguration.pkt`](./Ripconfiguration.pkt) | Saved Cisco Packet Tracer topology and configuration |
| `media/05-r1-show-ip-interface-brief.png` | R1 interface IPs and status; upload this file to display it |
| `media/06-r1-show-ip-route.png` | R1 routing table; upload this file to display it |
| `media/07-r1-show-ip-protocols.png` | R1 RIP v2 protocol output; upload this file to display it |
| `media/08-pc0-ping-r0.png` | PC0 ping evidence for R0; upload this file to display it |
| `media/09-pc0-ping-r1.png` | PC0 ping evidence for R1; upload this file to display it |
| `media/10-pc0-ping-r2.png` | PC0 ping evidence for R2; capture and upload this test |
| Practical video | Not yet present in this folder; upload it and add its exact filename above |

## 13. What We Learned

This practical helped us understand how to connect multiple LANs through routers and how dynamic routing allows routers to learn about remote networks. We practised checking interface addresses and status, reading route codes, verifying RIP v2 settings and using ping to test reachability between local and remote router interfaces.

We also reviewed the roles of ARP and ICMP. ARP resolves local next-hop MAC addresses, while ICMP supports ping-based connectivity checks. Simulation Mode can display packet events step by step, helping explain how packets cross switches and routers.

## 14. Result

The saved topology and supplied R0/R1 command outputs document a multi-router network using RIP v2. The two supplied PC0 ping tests—to R0 and R1—show 0% packet loss. The PC0-to-R2 result and any video demonstration should be added after the corresponding evidence is uploaded.
