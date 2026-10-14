# Simulation of ARP, ICMP and RIP v2 Routing

> **Networking Practical | Cisco Packet Tracer | Dynamic Routing | Packet Analysis**

## 1. Practical Overview

This practical demonstrates how a small multi-router network can be configured and tested in **Cisco Packet Tracer**. The topology contains three routers (R0, R1 and R2), three switches and six PCs. Each router connects a local LAN, while serial links connect the routers to one another.

The main purpose is to understand how devices communicate across different IP networks, how routers learn remote routes through **Routing Information Protocol version 2 (RIP v2)**, and how **ARP** and **ICMP** behave when packets are sent across the topology. The router command outputs and PC ping tests provide evidence that interfaces are configured, routes are being learned, and connectivity can be checked.

## 2. Practical Details

| Item | Details |
|---|---|
| **Practical name** | Simulation of ARP, ICMP and Routing Process Using Cisco Packet Tracer |
| **Software** | Cisco Packet Tracer |
| **Network devices** | 3 routers, 3 switches and 6 PCs |
| **Routing protocol** | RIP version 2 |
| **Network links** | Ethernet LAN links and serial router-to-router links |
| **Main concepts** | IPv4 addressing, interface status, routing tables, RIP v2, ARP, ICMP and Simulation Mode |
| **Verification** | `show ip interface brief`, `show ip route`, `show ip protocols` and ping tests |

## 3. Objective

To build a multi-router network and observe how ARP, ICMP and RIP v2 work in Cisco Packet Tracer. The practical aims to:

- Connect PCs to switches and switches to routers.
- Connect the routers using serial links.
- Configure IPv4 addresses on router interfaces and end devices.
- Enable RIP v2 so routers can exchange routing information dynamically.
- Check interface status and IP address assignments.
- Inspect connected and RIP-learned routes in each routing table.
- Use ping to test reachability between router interfaces across the network.
- Use Simulation Mode to inspect packet movement and understand ARP and ICMP events.

## 4. Network Topology

The topology is arranged as three LANs connected through three routers.

- **R0** connects to the left-side switch and its two PCs.
- **R1** connects to the middle switch and its two PCs.
- **R2** connects to the right-side switch and its two PCs.
- Serial links connect R0 to R1 and R1 to R2.
- RIP v2 exchanges routes between the routers so that each router can learn about networks that are not directly connected to it.

### Topology Screenshot

![Three-router RIP v2 topology](https://github.com/user-attachments/assets/5f083d99-e642-49ba-9808-38153150785c)

**What to look for:** the three LAN sections, router-to-switch connections, six end devices and the two serial connections between routers.

## 5. IP Addressing and Routing Overview

The screenshots show these LAN networks and router addresses:

| Network / Link | Network or address | Purpose |
|---|---|---|
| R0 LAN | `192.168.1.0/24` | Local network connected to R0 |
| R1 LAN | `192.168.2.0/24` | Local network connected to R1 |
| R2 LAN | `192.168.3.0/24` | Local network connected to R2 |
| R0–R1 serial link | `10.0.0.0/30` | Point-to-point router connection |
| R1–R2 serial link | `10.0.0.4/30` | Point-to-point router connection |

Router LAN interface addresses used in the connectivity tests:

- R0 LAN interface: `192.168.1.1`
- R1 LAN interface: `192.168.2.1`
- R2 LAN interface: `192.168.3.1`

A `/24` LAN uses subnet mask `255.255.255.0`; a `/30` serial network uses subnet mask `255.255.255.252`. Use the actual addresses in your Packet Tracer file if your final saved configuration differs.

## 6. Practical Demonstration Video

**▶️ [Watch / download the RIP v2 practical video](./media/Screen%20Recording%202026-10-01%20211929.mp4)**

The video is intended to show the practical setup and/or its verification in Cisco Packet Tracer. If the link does not open, check that the MP4 is uploaded to the `media` folder with the exact filename shown above. GitHub may not preview a large MP4 inline, but the file link can still be used to open or download it.

## 7. Router R0 — Verification Evidence

The following outputs were captured on **R0**.

### 7.1 R0 Network Topology

![R0 network topology](https://github.com/user-attachments/assets/f3f0338a-6476-4539-be27-b6daf06a07f9)

This image shows the left-side LAN connected to R0 and the serial connection toward the next router.

### 7.2 R0 — `show ip interface brief`

![R0 show ip interface brief](https://github.com/user-attachments/assets/66300f19-c31b-4758-aa2d-67ddc4736a2b)

**Purpose:** lists router interfaces, their assigned IP addresses and their line/protocol status.

The captured output shows:

- FastEthernet0/0: `192.168.1.1`, **up/up**
- Serial0/1/0: `10.0.0.1`, **up/up**
- FastEthernet0/1 and Serial0/1/1 are administratively down in this output.

**Interpretation:** the active LAN and serial interfaces are operational in the captured state. An interface showing `administratively down` has been disabled and is not currently being used.

### 7.3 R0 — `show ip route`

![R0 show ip route](https://github.com/user-attachments/assets/aeb0ee86-6d13-4a31-9009-81d2a14fc5ec)

**Purpose:** displays routes that R0 can use to forward packets.

Important route codes:

- `C` — directly connected network.
- `R` — route learned through RIP.
- `L` — local interface address, where displayed by the router.

The captured table includes R0's directly connected LAN and serial network, plus remote networks learned through RIP. This is evidence that routing information from other routers has reached R0.

### 7.4 R0 — `show ip protocols`

![R0 show ip protocols](https://github.com/user-attachments/assets/b47eb815-2b59-4387-85a1-8542a0c809e5)

**Purpose:** verifies which routing protocol is running and what networks are included in its configuration.

The captured output indicates:

- Routing protocol: `rip`
- RIP version 2 is configured to send and receive updates.
- Networks listed for R0 include `10.0.0.0` and `192.168.1.0`.
- Routing information is received from next-hop address `10.0.0.2`.

## 8. Router R1 — Verification Evidence

The following filenames are reserved for the R1 screenshots. Upload each screenshot to the `media` folder using the exact filename so the links below display correctly.

### 8.1 R1 — `show ip interface brief`

![R1 show ip interface brief](./media/05-r1-show-ip-interface-brief.png)

**Purpose:** checks the IP address and operational status of each R1 interface.

The supplied R1 output shows:

- FastEthernet0/0: `192.168.2.1`, **up/up**
- Serial0/1/0: `10.0.0.2`, **up/up**
- Serial0/1/1: `10.0.0.5`, **up/up**

These active interfaces connect R1 to its LAN and to the serial networks on either side.

### 8.2 R1 — `show ip route`

![R1 show ip route](./media/06-r1-show-ip-route.png)

**Purpose:** checks R1's directly connected networks and the remote networks learned from R0 and R2.

The supplied output includes connected networks and RIP routes for remote LAN/serial networks. RIP-learned entries are marked with `R`; the next-hop address and outgoing interface indicate where R1 forwards traffic.

### 8.3 R1 — `show ip protocols`

![R1 show ip protocols](./media/07-r1-show-ip-protocols.png)

**Purpose:** confirms that RIP is active and shows the RIP version, networks being advertised and routing information sources.

The supplied output indicates RIP version 2 send/receive behaviour, networks including `10.0.0.0` and `192.168.2.0`, and routing information sources `10.0.0.1` and `10.0.0.6`.

## 9. PC0 Connectivity Tests

Ping sends ICMP Echo Requests and checks whether ICMP Echo Replies return. The following tests are documented from PC0.

### 9.1 PC0 to R0

Command:

```text
ping 192.168.1.1
```

![PC0 ping to R0](./media/08-pc0-ping-r0.png)

**Captured result:** 4 packets sent, 4 received, 0% packet loss. This confirms connectivity from PC0 to R0's LAN interface in the captured test.

### 9.2 PC0 to R1

Command:

```text
ping 192.168.2.1
```

![PC0 ping to R1](./media/09-pc0-ping-r1.png)

**Captured result:** 4 packets sent, 4 received, 0% packet loss. This demonstrates that PC0 can reach R1's LAN interface through the routed network.

### 9.3 PC0 to R2

Command:

```text
ping 192.168.3.1
```

![PC0 ping to R2](./media/10-pc0-ping-r2.png)

**Evidence status:** add the screenshot of the completed command and its ping statistics after running this test. Do not mark this test successful until the actual output confirms replies.

## 10. Procedure — Step by Step

1. Open Cisco Packet Tracer and create or open the three-router topology.
2. Place three routers, three switches and six PCs in the workspace.
3. Connect two PCs to each switch using Ethernet connections.
4. Connect each switch to its local router using Ethernet connections.
5. Connect R0 to R1 and R1 to R2 using serial links. Confirm that the routers have the required serial interfaces.
6. Assign the correct IPv4 addresses and subnet masks to router interfaces.
7. Configure each PC with an IP address, subnet mask and the default gateway for its LAN.
8. Bring the required router interfaces up with the appropriate interface configuration commands.
9. Configure RIP version 2 on each router and advertise the directly connected LAN and serial networks used in the topology.
10. Allow RIP updates to propagate, then run `show ip interface brief` on each router to verify interface status.
11. Run `show ip protocols` to check that RIP v2 is enabled and the expected networks are included.
12. Run `show ip route` to confirm that remote routes appear with the RIP route code `R`.
13. From PC0, open the command prompt and run the ping tests for `192.168.1.1`, `192.168.2.1` and `192.168.3.1`.
14. To inspect packet behaviour, switch to **Simulation** mode and filter for ARP and ICMP events.
15. Create a Simple PDU between a source PC and destination PC, then use **Capture / Forward** to step through the events.
16. Open event details to inspect packet information and observe how traffic is forwarded hop by hop.
17. Save the Packet Tracer project and capture screenshots of the topology, router commands, ping results and simulation events.

## 11. ARP, ICMP and RIP v2 — Main Concepts

### ARP (Address Resolution Protocol)

ARP helps a device discover the MAC address associated with a local IPv4 address before sending an Ethernet frame on the local network. In Simulation Mode, an ARP request and reply may appear when the sender needs to resolve a next-hop address.

### ICMP (Internet Control Message Protocol)

ICMP supports network diagnostics and error reporting. The `ping` command uses ICMP Echo Request and Echo Reply messages to test reachability. Successful ping replies show that the destination responded to the test; they do not alone prove every application or service is working.

### RIP v2 (Routing Information Protocol version 2)

RIP v2 is a distance-vector dynamic routing protocol. Routers exchange route information with neighbouring routers and use hop count as the route metric. The `show ip route` and `show ip protocols` commands help verify learned routes and protocol configuration.

## 12. File Guide — What Each File Is For

| File or path | Main purpose |
|---|---|
| `README.md` | Main practical report: overview, objective, topology, procedure, screenshots, tests and learning outcomes. |
| `Ripconfiguration.pkt` | Cisco Packet Tracer project file containing the network topology and device configuration. Open it in Packet Tracer to inspect or repeat the practical. |
| `media/Screen Recording 2026-10-01 211929.mp4` | Intended location for the practical demonstration video. Upload the matching MP4 to this folder for the link above to work. |
| `media/05-r1-show-ip-interface-brief.png` | R1 interface IP addresses and interface/protocol status. |
| `media/06-r1-show-ip-route.png` | R1 routing table, including connected and RIP-learned routes. |
| `media/07-r1-show-ip-protocols.png` | R1 RIP v2 version, advertised networks and routing information sources. |
| `media/08-pc0-ping-r0.png` | PC0 ping output for R0 at `192.168.1.1`. |
| `media/09-pc0-ping-r1.png` | PC0 ping output for R1 at `192.168.2.1`. |
| `media/10-pc0-ping-r2.png` | PC0 ping output for R2 at `192.168.3.1`; capture and upload this evidence after running the test. |

### Recommended folder structure

```text
03-RIP-v2-Simulation/
├── README.md
├── Ripconfiguration.pkt
└── media/
    ├── Screen Recording 2026-10-01 211929.mp4
    ├── 05-r1-show-ip-interface-brief.png
    ├── 06-r1-show-ip-route.png
    ├── 07-r1-show-ip-protocols.png
    ├── 08-pc0-ping-r0.png
    ├── 09-pc0-ping-r1.png
    └── 10-pc0-ping-r2.png
```

**Important:** the R0 images above are embedded directly in this README using GitHub attachment URLs. The R1 and PC0 image links in the table are filenames to use when uploading those image files into `media/`.

## 13. What We Learned

By completing this practical, we learned how to build and document a network with multiple routers, switches and end devices. We practised assigning IPv4 addresses, checking interface status and verifying that serial and Ethernet links are operational. We also learned how to read a routing table and distinguish directly connected routes from routes learned dynamically through RIP.

The practical reinforced how RIP v2 allows routers to exchange network information without manually adding every remote route. The `show ip protocols` output helps confirm the routing protocol and advertised networks, while `show ip route` provides evidence of routes learned from neighbouring routers. The PC0 ping tests demonstrate how ICMP can be used to check reachability to router interfaces on local and remote networks.

Finally, Simulation Mode provides a visual way to study ARP resolution and ICMP packet movement through the topology. Combining the Packet Tracer project, command outputs, connectivity tests, screenshots and video creates a repeatable record of the practical.

## 14. Result

A three-router, three-switch and six-PC topology was prepared in Cisco Packet Tracer, and RIP v2 configuration was verified in the supplied R0 and R1 outputs. The recorded PC0 tests to R0 and R1 completed with 0% packet loss. The PC0-to-R2 test should be recorded separately and added to the evidence section after it has been run. The practical covers ARP, ICMP and dynamic route learning with RIP v2.
