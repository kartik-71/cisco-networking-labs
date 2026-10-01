# Practical: Simulation of ARP, ICMP and RIP v2 Routing

## 📌 Practical Name

**Simulation of ARP, ICMP and Routing Process Using Cisco Packet Tracer**

## 🎯 Objective

To create a multi-router network in Cisco Packet Tracer and observe how **ARP, ICMP, and RIP v2** packets travel through the network using **Simulation Mode**.

## 🎥 Practical Demonstration Video

**▶️ [Watch / Download the RIP v2 Simulation Video](./media/Screen%20Recording%202026-10-01%20211929.mp4)**

> If GitHub does not preview the MP4 directly, click the link above to open or download the video.

---

## 🌐 Network Topology

The practical consists of:

- **3 Routers** — R0, R1, R2
- **3 Switches**
- **6 PCs** — PC0 to PC5
- Ethernet connections between PCs, switches and routers
- Serial connections between routers
- **RIP version 2** for dynamic routing

### Topology

![RIP v2 Network Topology](./media/01-rip-v2-network-topology.png)

---

## ⚙️ Routing and Verification

The practical uses **RIP version 2** to exchange routing information between the routers.

### 1. Verify Router Interfaces

The `show ip interface brief` command was used to check the configured interfaces and their status.

![Show IP Interface Brief](./media/02-show-ip-interface-brief.png)

The screenshot shows:

- FastEthernet0/0 — `192.168.1.1`
- Serial0/1/0 — `10.0.0.1`
- The shown active interfaces have **Status: up** and **Protocol: up**

---

### 2. Check the Routing Table

The `show ip route` command was used to observe routes learned by the router.

![Show IP Route](./media/03-show-ip-route.png)

The routing table shows RIP-learned routes marked with **R**, including routes to:

- `10.0.0.4/30`
- `192.168.2.0/24`
- `192.168.3.0/24`

The routes are learned through the next-hop router using RIP.

---

### 3. Verify RIP v2

The `show ip protocols` command was used to verify the routing protocol configuration.

![Show IP Protocols](./media/04-show-ip-protocols.png)

The screenshot shows:

- Routing Protocol: **rip**
- **Send version 2, receive version 2**
- Routing network: `10.0.0.0`
- Routing network: `192.168.1.0`
- Routing information source: `10.0.0.2`

---

## 🔬 Simulation Mode

The practical can be observed using the **Simulation** tab in Cisco Packet Tracer.

### Steps

1. Open the completed topology in Cisco Packet Tracer.
2. Select the **Simulation** tab.
3. Keep the event filters required for **ARP** and **ICMP**.
4. Create a **Simple PDU** from a source PC to a destination PC.
5. Start the simulation.
6. Use **Capture / Forward** to observe each packet step-by-step.
7. Observe how ARP resolves the destination MAC address on the local network.
8. Observe the ICMP packet as it travels through the routers.
9. Observe the routing path selected using RIP v2.
10. Check the packet details at each hop.

---

## 📸 Screenshots

### Network Topology

![Network Topology](./media/01-rip-v2-network-topology.png)

### Show IP Interface Brief

![Show IP Interface Brief](./media/02-show-ip-interface-brief.png)

### Show IP Route

![Show IP Route](./media/03-show-ip-route.png)

### Show IP Protocols — RIP v2

![Show IP Protocols](./media/04-show-ip-protocols.png)

---

## 🧠 What We Learned

From this practical, we learned:

- How to create a multi-router network in **Cisco Packet Tracer**.
- How routers, switches and PCs communicate in a network.
- How **RIP v2** is used for dynamic routing.
- How routers learn remote networks through RIP.
- How to use `show ip interface brief` to verify interface status and IP addresses.
- How to use `show ip route` to inspect the routing table.
- How to use `show ip protocols` to verify RIP configuration and version.
- How **ARP** is used to resolve IP addresses to MAC addresses on a local network.
- How **ICMP** is used for network connectivity testing.
- How to use **Simulation Mode** to observe packets travelling hop-by-hop.
- How routing information determines the path followed by packets between different networks.

---

## 📁 Practical Files

- **Packet Tracer file:** `RIP-v2-Simulation.pkt` *(add the file here if required)*
- **Video:** [RIP v2 Simulation Video](./media/Screen%20Recording%202026-10-01%20211929.mp4)
- **Topology screenshot:** [01-rip-v2-network-topology.png](./media/01-rip-v2-network-topology.png)
- **Interface verification:** [02-show-ip-interface-brief.png](./media/02-show-ip-interface-brief.png)
- **Routing table:** [03-show-ip-route.png](./media/03-show-ip-route.png)
- **RIP verification:** [04-show-ip-protocols.png](./media/04-show-ip-protocols.png)

---

## ✅ Result

The multi-router topology was configured in Cisco Packet Tracer and RIP v2 was verified. The practical demonstrates how **ARP, ICMP and dynamic routing information** can be observed through Packet Tracer's Simulation Mode.
