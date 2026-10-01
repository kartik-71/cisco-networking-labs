# Practical: Simulation of ARP, ICMP and RIP v2 Routing

## 📌 Practical Name

**Simulation of ARP, ICMP and Routing Process Using Cisco Packet Tracer**

## 🎯 Objective

To create a multi-router network in Cisco Packet Tracer and observe how **ARP, ICMP, and RIP v2** packets travel through the network using **Simulation Mode**.

## 🎥 Practical Demonstration Video

**▶️ [Watch / Download the RIP v2 Simulation Video](./media/Screen%20Recording%202026-10-01%20211929.mp4)**

> The video link is placed near the top so it is easy to find. If GitHub does not preview the MP4 directly, click the link to open or download it.

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

![RIP v2 Network Topology]<img width="842" height="502" alt="image" src="https://github.com/user-attachments/assets/5f083d99-e642-49ba-9808-38153150785c" />


---

# 🖥️ R0 Verification Screenshots

The following screenshots are from **Router R0**.

## 1. R0 — Network Topology

![R0 Network Topology]<img width="842" height="502" alt="image" src="https://github.com/user-attachments/assets/f3f0338a-6476-4539-be27-b6daf06a07f9" />


The topology shows R0 connected to the local switch and PCs, with a serial connection from R0 toward R1.

---

## 2. R0 — Show IP Interface Brief

The `show ip interface brief` command was used to check the configured interfaces, IP addresses, and interface status.

![R0 Show IP Interface Brief]<img width="701" height="132" alt="Screenshot 2026-10-01 213523" src="https://github.com/user-attachments/assets/66300f19-c31b-4758-aa2d-67ddc4736a2b" />


The screenshot shows:

- FastEthernet0/0 — `192.168.1.1`
- Serial0/1/0 — `10.0.0.1`
- FastEthernet0/0 — **up/up**
- Serial0/1/0 — **up/up**

---

## 3. R0 — Show IP Route

The `show ip route` command was used to view the routing table and routes learned through RIP.

![R0 Show IP Route]<img width="667" height="290" alt="Screenshot 2026-10-01 213622" src="https://github.com/user-attachments/assets/aeb0ee86-6d13-4a31-9009-81d2a14fc5ec" />


The routing table shows RIP-learned routes marked with **R**, including remote networks reached through the next-hop router.

---

## 4. R0 — Show IP Protocols

The `show ip protocols` command was used to verify the routing protocol configuration.

![R0 Show IP Protocols]<img width="512" height="331" alt="Screenshot 2026-10-01 213702" src="https://github.com/user-attachments/assets/b47eb815-2b59-4387-85a1-8542a0c809e5" />


The screenshot shows:

- Routing Protocol: **rip**
- **Send version 2, receive version 2**
- Routing networks:
  - `10.0.0.0`
  - `192.168.1.0`
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

### R0 — Network Topology

![Network Topology]<img width="842" height="502" alt="Screenshot 2026-10-01 212005" src="https://github.com/user-attachments/assets/46790300-8b88-4cce-a4b4-ac23c0437185" />


### R0 — Show IP Interface Brief

![Show IP Interface Brief]<img width="701" height="132" alt="Screenshot 2026-10-01 213523" src="https://github.com/user-attachments/assets/c0d300a8-e856-41f9-92cf-a60f75da0491" />


### R0 — Show IP Route

![Show IP Route]<img width="667" height="290" alt="Screenshot 2026-10-01 213622" src="https://github.com/user-attachments/assets/3d3b17a9-c9bc-4f83-9fc5-f1d2b4c3cb05" />


### R0 — Show IP Protocols — RIP v2

![Show IP Protocols]<img width="512" height="331" alt="Screenshot 2026-10-01 213702" src="https://github.com/user-attachments/assets/a7fc7afe-413d-48ba-a822-739126bedcf0" />


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
- How to verify RIP v2 configuration on an individual router such as **R0**.

---

## 📁 Practical Files

- **Packet Tracer file:** `RIP-v2-Simulation.pkt` *(add the file here if required)*
- **Video:** [RIP v2 Simulation Video](./media/Screen%20Recording%202026-10-01%20211929.mp4)
- **Topology:** [R0 Network Topology](./media/01-rip-v2-network-topology.png)
- **R0 Interface Verification:** [show ip interface brief](./media/02-r0-show-ip-interface-brief.png)
- **R0 Routing Table:** [show ip route](./media/03-r0-show-ip-route.png)
- **R0 RIP Verification:** [show ip protocols](./media/04-r0-show-ip-protocols.png)

---

## ✅ Result

The multi-router topology was configured in Cisco Packet Tracer and RIP v2 was verified on R0. The practical demonstrates how **ARP, ICMP and dynamic routing information** can be observed through Packet Tracer's Simulation Mode.
