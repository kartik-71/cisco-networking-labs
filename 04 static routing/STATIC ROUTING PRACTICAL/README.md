# Static Routing Between Networks

> **Cisco Packet Tracer · IPv4 routing · Static routes · Network verification**

## 1. Practical Overview

This practical explores static routing in Cisco Packet Tracer. Static routing uses routes entered manually by a network administrator to tell a router how to reach a remote network. The lab involves connecting routers and LANs, configuring IPv4 addresses and entering destination network, subnet mask and next-hop information.

The folder contains the practical screen recording and screenshots captured during configuration. Review the saved evidence alongside the steps below.

## 2. Practical Details

| Item | Details |
|---|---|
| Practical name | Static Routing Between Networks |
| Software | Cisco Packet Tracer |
| Main topic | Manually configured IPv4 routes |
| Key concepts | Router interfaces, LAN addressing, subnet masks, destination network, next hop and routing table |
| Verification | `show ip interface brief`, `show ip route` and ping tests where performed |

## 3. Objective

To understand how routers forward packets to remote networks using manually configured static routes, and to practise configuring interfaces and checking routing information in Packet Tracer.

## 4. Network Topology

The practical uses multiple routers connected together, with LANs attached to router interfaces. Each LAN requires an appropriate IPv4 network and subnet mask. For communication between different LANs, the routers need routes that identify where packets for remote destination networks should be sent.

### Topology and configuration evidence

- [Screenshot 1 — Screenshot 2026-10-03 171240.png](./Screenshot%202026-10-03%20171240.png)
- [Screenshot 2 — Screenshot 2026-10-03 171519.png](./Screenshot%202026-10-03%20171519.png)
- [Screenshot 3 — Screenshot 2026-10-03 171541.png](./Screenshot%202026-10-03%20171541.png)
- [Screenshot 4 — Screenshot 2026-10-03 171604.png](./Screenshot%202026-10-03%20171604.png)

## 5. Static Routing Concept

A static route identifies:

1. **Destination network** — the remote network that must be reached.
2. **Subnet mask** — identifies the size of that destination network.
3. **Next-hop IP address** — the neighbouring router to which packets should be forwarded, or the appropriate outgoing interface.

The generic Cisco IOS command format is:

```text
ip route <destination-network> <subnet-mask> <next-hop-ip>
```

For example, the values entered must match the actual addressing plan and the reachable next-hop address in the Packet Tracer topology. This README does not invent a specific route table that is not visible in the screenshots.

## 6. Procedure

1. Open Cisco Packet Tracer and create or open the static-routing topology.
2. Place the routers and end devices required by the topology.
3. Connect routers to one another and connect each LAN to its router using the appropriate interfaces and cables.
4. Inspect the available router ports and confirm that the selected interfaces support the planned connections.
5. Assign IPv4 addresses and subnet masks to the router interfaces.
6. Enable the required interfaces and check their status.
7. Configure the IP address, subnet mask and default gateway on each PC.
8. Identify the remote networks that are not directly connected to each router.
9. Add a static route for each required remote network using the destination network, mask and next-hop IP address.
10. Run `show ip interface brief` to check interface status and IP assignments.
11. Run `show ip route` to confirm that the static routes appear in the routing table.
12. Use ping between suitable devices or router interfaces to test end-to-end connectivity.
13. If a ping fails, verify the IP addresses, masks, interface state, next-hop address, return route and PC default gateway.
14. Save the Packet Tracer project and retain the screenshots and screen recording as evidence.

## 7. Verification Commands

### Interface status

```text
show ip interface brief
```

Use this command to check interface IP addresses and determine whether the required interfaces are up.

### Routing table

```text
show ip route
```

A static route is typically marked with **S** in the Cisco routing table. Directly connected networks are marked with **C**. Confirm the actual route entries in the router output.

### Connectivity test

```text
ping <destination-ip>
```

Ping checks whether the destination responds to ICMP Echo Requests. A successful test is useful evidence of reachability between the tested endpoints.

## 8. Screenshots

### Screenshot 1 — Initial practical evidence

![Static routing screenshot 1](./Screenshot%202026-10-03%20171240.png)

### Screenshot 2 — Router configuration evidence

![Static routing screenshot 2](./Screenshot%202026-10-03%20171519.png)

### Screenshot 3 — Routing configuration evidence

![Static routing screenshot 3](./Screenshot%202026-10-03%20171541.png)

### Screenshot 4 — Additional verification evidence

![Static routing screenshot 4](./Screenshot%202026-10-03%20171604.png)

The filenames are retained as uploaded so that each image can be matched with the original capture.

## 9. Practical Demonstration Video

**[▶️ Watch / download the Static Routing practical video](./Screen%20Recording%202026-10-03%20171408.mp4)**

The recording shows the practical work. Use the video together with the screenshots to review the configuration sequence.

## 10. File Guide

| File | Purpose |
|---|---|
| `README.md` | Main report containing the overview, static routing explanation, procedure, evidence and learning outcomes |
| `Screen Recording 2026-10-03 171408.mp4` | Video demonstration of the practical |
| `Screenshot 2026-10-03 171240.png` | First captured screenshot |
| `Screenshot 2026-10-03 171519.png` | Second captured screenshot |
| `Screenshot 2026-10-03 171541.png` | Third captured screenshot |
| `Screenshot 2026-10-03 171604.png` | Fourth captured screenshot |

## 11. What We Learned

- How static routing enables communication with remote networks.
- How to identify a destination network and its subnet mask.
- Why a static route needs a reachable next-hop address or outgoing interface.
- How to configure router interfaces and check whether they are operational.
- How to inspect the routing table and identify static route entries.
- How end devices use default gateways to reach other networks.
- How to test network reachability with ping.
- How to troubleshoot static routing by checking both the forward and return paths.
- How to document a practical using screenshots and a screen recording.

## 12. Result

The practical demonstrates the main steps involved in preparing a multi-router topology and documenting static routing in Packet Tracer. The route entries and ping results should be checked against the saved topology to confirm that each intended remote network is reachable.
