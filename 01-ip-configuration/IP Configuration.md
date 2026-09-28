# Practical 01 — IP Configuration and Basic Routing

## Aim

To create a small network using **2 routers, 2 switches and 6 PCs**, configure IPv4 addresses, connect the networks through a serial link, configure routing, and verify connectivity using Cisco Packet Tracer.

---

## Requirements

- Cisco Packet Tracer
- 2 Routers
- 2 Switches
- 6 PCs
- Copper Ethernet cables
- Serial cable between the routers

---

# Procedure

## Step 1 — Open Cisco Packet Tracer

1. Open **Cisco Packet Tracer** on the computer.
2. Wait for the Packet Tracer workspace to load.
3. Keep the **Logical** workspace selected.

---

## Step 2 — Add the Routers

1. At the bottom-left of Packet Tracer, open **Network Devices**.
2. Select **Routers**.
3. Choose the router model required for the practical.
4. Drag **two routers** into the workspace.
5. Name them **Router A** and **Router B**.

---

## Step 3 — Add the Switches

1. Select **Switches** from the Network Devices section.
2. Add **two switches** to the workspace.
3. Place one switch near Router A and the other near Router B.

The layout should be similar to:

```text
PC0   PC1   PC2
 |     |     |
 +-----+-----+
       |
    Switch 1
       |
   Router A
       |
   Serial Link
       |
   Router B
       |
    Switch 2
 +-----+-----+
 |     |     |
PC3   PC4   PC5
```

---

## Step 4 — Add the PCs

1. Select **End Devices**.
2. Select **PC**.
3. Add **six PCs** to the workspace.
4. Place three PCs on the left side and three PCs on the right side.
5. Keep the devices arranged clearly so that the network is easy to troubleshoot.

---

## Step 5 — Connect the PCs to the Switches

1. Select **Connections** (the lightning-bolt icon).
2. Select the appropriate Ethernet cable.
3. Connect each PC to a switch.
4. Connect the three left-side PCs to Switch 1.
5. Connect the three right-side PCs to Switch 2.

Wait for the link indicators to become active.

---

## Step 6 — Connect the Switches to the Routers

1. Use an Ethernet cable.
2. Connect **Switch 1** to Router A's FastEthernet interface.
3. Connect **Switch 2** to Router B's FastEthernet interface.
4. Check that the interfaces become active.

---

## Step 7 — Connect Router A and Router B

1. Use the appropriate **serial connection** between the routers.
2. Connect Router A's **Serial0/1/0** to Router B's **Serial0/1/0**.
3. The serial network used in this practical is:

```text
10.0.0.0/30
```

---

# Step 8 — Configure Router A

Open Router A → **CLI**.

Enter the following configuration:

```text
enable
configure terminal

interface fastethernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface serial 0/1/0
ip address 10.0.0.1 255.255.255.252
no shutdown
exit
```

If Router A is the DCE side of the serial connection, configure the clock rate:

```text
interface serial 0/1/0
clock rate 64000
```

---

# Step 9 — Configure Router B

Open Router B → **CLI**.

Enter:

```text
enable
configure terminal

interface fastethernet 0/0
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

interface serial 0/1/0
ip address 10.0.0.2 255.255.255.252
no shutdown
exit
```

If Router B is the DCE side instead, configure the clock rate on Router B's serial interface.

---

# Step 10 — Configure the PCs

Open each PC → **Desktop** → **IP Configuration**.

Configure each PC with:

- IPv4 address
- Subnet mask
- Default gateway

For the left LAN, use the **192.168.1.0/24** network and Router A's **192.168.1.1** as the default gateway.

For the right LAN, use the **192.168.2.0/24** network and Router B's **192.168.2.1** as the default gateway.

Make sure every PC has a unique IP address.

---

# Step 11 — Configure Static Routing

Router A needs a route to the right-side LAN:

```text
enable
configure terminal
ip route 192.168.2.0 255.255.255.0 10.0.0.2
end
```

Router B needs a route to the left-side LAN:

```text
enable
configure terminal
ip route 192.168.1.0 255.255.255.0 10.0.0.1
end
```

This allows traffic to travel between the two different LANs.

---

# Step 12 — Verify the Router Interfaces

On the router CLI, run:

```text
show ip interface brief
```

This command displays the interfaces, IP addresses, status and protocol.

The practical result shows Router A with:

| Interface | IP Address | Status | Protocol |
|---|---|---|---|
| FastEthernet0/0 | 192.168.1.1 | up | up |
| Serial0/1/0 | 10.0.0.1 | up | up |

The other unused interfaces are shown as unassigned/administratively down.

---

# Step 13 — Check the Routing Table

Run:

```text
show ip route
```

The routing table shows connected networks and the configured static route.

The practical result includes:

```text
C 10.0.0.0/30 is directly connected, Serial0/1/0
C 192.168.1.0/24 is directly connected, FastEthernet0/0
S 192.168.2.0/24 [1/0] via 10.0.0.2
```

The **S** entry represents a static route to the 192.168.2.0/24 network through 10.0.0.2.

---

# Step 14 — Test Connectivity from a PC

Open a PC → **Desktop** → **Command Prompt**.

Test the local network:

```text
ping 192.168.1.11
```

The captured result shows:

```text
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)
```

This confirms successful connectivity to the destination.

---

# Step 15 — Test Communication Between the Two LANs

From a PC on the left network, test a PC on the right network.

Example:

```text
ping 192.168.2.10
```

The captured test initially showed one timeout followed by successful replies:

```text
Reply from 192.168.2.10
Reply from 192.168.2.10
Reply from 192.168.2.10
```

This demonstrates communication across the routed networks. An initial timeout can occur while the network is resolving/learning the required information.

---

# Step 16 — Use Cisco Packet Tracer Simulation Mode

1. Click **Simulation** in the bottom-right of Packet Tracer.
2. Click **Add Simple PDU** (the envelope icon).
3. Click the source PC, for example **PC0**.
4. Click the destination PC, for example **PC3**.
5. Packet Tracer creates a test packet.
6. Use **Capture/Forward** to move through the packet-processing steps.
7. Observe the packet as it travels from the source PC to the switch, router, serial link, next router, switch and destination PC.
8. Inspect the events for **ARP** and **ICMP**.

The packet flow can be observed as:

```text
PC0
 ↓
ARP / MAC resolution
 ↓
Switch
 ↓
Router A
 ↓
Routing Table Lookup
 ↓
Serial Link
 ↓
Router B
 ↓
Switch
 ↓
PC3
 ↓
ICMP Reply
```

---

# Step 17 — Save the Packet Tracer File

1. Select **File → Save As**.
2. Save the practical as:

```text
01-IP-Configuration.pkt
```

3. Keep the Packet Tracer file together with the practical documentation.

---

# Results / Evidence

## 1. PC-to-PC Ping

The captured result shows successful communication to **192.168.1.11** with:

- 4 packets sent
- 4 packets received
- 0% packet loss

![PC0 ping result](media/pc0-ping-pc1.png)

---

## 2. Cross-Network Ping

A ping to **192.168.2.10** was tested from the PC command prompt. The captured output shows an initial timeout followed by successful replies.

![Cross-network ping result](media/ping-pc3.png)

---

## 3. Routing Table

The Router CLI output shows the connected networks and the static route:

```text
S 192.168.2.0/24 [1/0] via 10.0.0.2
```

![show ip route](media/show-ip-route.png)

---

## 4. Interface Verification

The `show ip interface brief` command shows the configured interfaces as **up/up** for the active FastEthernet and Serial interfaces.

![show ip interface brief](media/show-ip-interface-brief.png)

---

## 5. Additional Connectivity Test

![Connectivity test](media/connectivity-test.png)

---

# Commands Used

```text
show ip interface brief
show ip route
ping 192.168.1.11
ping 192.168.2.10
```

---

# What We Learned

From this practical, we learned how to:

- Create a network topology in Cisco Packet Tracer.
- Add routers, switches and PCs.
- Connect network devices.
- Configure IPv4 addresses.
- Configure router interfaces.
- Bring interfaces up using `no shutdown`.
- Configure a serial connection between routers.
- Configure static routes.
- Understand routing-table entries.
- Test connectivity using `ping`.
- Verify interfaces using `show ip interface brief`.
- Verify routes using `show ip route`.
- Observe ARP and ICMP traffic in Simulation Mode.
- Understand how packets travel between different networks.
- Perform basic network troubleshooting.

---

# Practical Outcome

The two LANs were connected through two routers, and connectivity was verified using router commands, PC ping tests and Cisco Packet Tracer Simulation Mode.

> **Note:** The screenshots above are the evidence captured during the practical. The video recording should be placed in the same `media` folder and linked from this document once uploaded to the repository.
