# OSPF Practical — Three-Router Lab

> **Cisco Packet Tracer · 3 × Cisco 2911 routers · 2 × Cisco 2960 switches · OSPFv2 · Area 0**

## 1. Practical Overview

**Objective:** Configure OSPF so PC1 can communicate with PC2 through R1, R2 and R3. Verify router adjacencies, OSPF-learned routes and end-to-end connectivity.

**Result:** The submitted evidence shows OSPF neighbors reaching FULL states, OSPF routes installed on R1, and PC1 successfully pinging PC2 with **4 packets received and 0% loss**.

## 2. Topology

```text
PC1 — SW1 — R1 — R2 — R3 — SW2 — PC2
              |     |     |
           LAN 1  transit LAN 2
```

- LAN 1: `192.168.1.0/24`
- R1–R2 transit network: `10.0.12.0/30`
- R2–R3 transit network: `10.0.23.0/30`
- LAN 2: `192.168.2.0/24`
- OSPF process ID: `1`; area: `0`

## 3. IP Addressing Table

| Device | Interface | IP address | Subnet mask | Purpose |
|---|---|---|---|---|
| PC1 | NIC | `192.168.1.10` | `255.255.255.0` | LAN 1 host |
| R1 | G0/0 | `192.168.1.1` | `255.255.255.0` | PC1 gateway |
| R1 | G0/1 | `10.0.12.1` | `255.255.255.252` | R1–R2 |
| R2 | G0/0 | `10.0.12.2` | `255.255.255.252` | R1–R2 |
| R2 | G0/1 | `10.0.23.1` | `255.255.255.252` | R2–R3 |
| R3 | G0/0 | `10.0.23.2` | `255.255.255.252` | R2–R3 |
| R3 | G0/1 | `192.168.2.1` | `255.255.255.0` | PC2 gateway |
| PC2 | NIC | `192.168.2.10` | `255.255.255.0` | LAN 2 host |

## 4. Physical Connections

Use Copper Straight-Through for PC-to-switch and switch-to-router links. Direct router-to-router GigabitEthernet links can use Copper Cross-Over or Packet Tracer's automatic connection tool.

| From | Port | To | Port |
|---|---|---|---|
| PC1 | FastEthernet0 | SW1 | FastEthernet0/1 |
| SW1 | FastEthernet0/2 | R1 | GigabitEthernet0/0 |
| R1 | GigabitEthernet0/1 | R2 | GigabitEthernet0/0 |
| R2 | GigabitEthernet0/1 | R3 | GigabitEthernet0/0 |
| R3 | GigabitEthernet0/1 | SW2 | FastEthernet0/2 |
| SW2 | FastEthernet0/1 | PC2 | FastEthernet0 |

## 5. Router Configuration

### R1

```text
enable
configure terminal
hostname R1
interface gigabitEthernet 0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
interface gigabitEthernet 0/1
 ip address 10.0.12.1 255.255.255.252
 no shutdown
exit
router ospf 1
 router-id 1.1.1.1
 network 192.168.1.0 0.0.0.255 area 0
 network 10.0.12.0 0.0.0.3 area 0
end
```

### R2

```text
enable
configure terminal
hostname R2
interface gigabitEthernet 0/0
 ip address 10.0.12.2 255.255.255.252
 no shutdown
exit
interface gigabitEthernet 0/1
 ip address 10.0.23.1 255.255.255.252
 no shutdown
exit
router ospf 1
 router-id 2.2.2.2
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.23.0 0.0.0.3 area 0
end
```

### R3

```text
enable
configure terminal
hostname R3
interface gigabitEthernet 0/0
 ip address 10.0.23.2 255.255.255.252
 no shutdown
exit
interface gigabitEthernet 0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown
exit
router ospf 1
 router-id 3.3.3.3
 network 10.0.23.0 0.0.0.3 area 0
 network 192.168.2.0 0.0.0.255 area 0
end
```

## 6. PC Configuration

Set these values in **PC → Desktop → IP Configuration**.

**PC1**
- IP address: `192.168.1.10`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.1.1`

**PC2**
- IP address: `192.168.2.10`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.2.1`

## 7. Verification Procedure

On each router, use privileged EXEC mode and run:

```text
show ip interface brief
show ip ospf neighbor
show ip route
```

From PC1, open **Desktop → Command Prompt** and run:

```text
ping 192.168.2.10
```

## 8. Observed Results

### OSPF neighbors

- **R1:** neighbor ID `2.2.2.2`, state `FULL/BDR`, neighbor address `10.0.12.2`, interface `GigabitEthernet0/1`.
- **R2:** neighbor ID `1.1.1.1`, state `FULL/DR`, address `10.0.12.1`, interface `GigabitEthernet0/0`.
- **R2:** neighbor ID `3.3.3.3`, state `FULL/BDR`, address `10.0.23.2`, interface `GigabitEthernet0/1`.

### R1 routing table

The captured output confirms these important entries:

- `C 10.0.12.0/30` — directly connected to R1.
- `O 10.0.23.0/30 [110/2] via 10.0.12.2` — transit network learned through OSPF.
- `C 192.168.1.0/24` — local LAN directly connected.
- `O 192.168.2.0/24 [110/3] via 10.0.12.2` — remote LAN learned through OSPF.

### PC1-to-PC2 ping

The submitted test shows four replies from `192.168.2.10`:

- Packets sent: 4
- Packets received: 4
- Packets lost: 0
- Loss: **0%**

This verifies end-to-end connectivity across all three routers.

## 9. Screenshots

The screenshot evidence supplied for this practical includes:

1. Complete topology showing PC1, SW1, R1, R2, R3, SW2 and PC2.
2. R1 routing table showing the OSPF-learned transit and remote LAN routes.
3. PC1 ping output showing 4/4 replies and 0% packet loss.
4. R1 OSPF neighbor output showing R2 in FULL state.
5. R2 OSPF neighbor output showing R1 and R3 in FULL states.

The screenshot bundle is maintained separately as **OSPF_Screenshots.pdf**.

## 10. Important OSPF Commands

| Command | Purpose |
|---|---|
| `show ip ospf neighbor` | View OSPF neighbors and adjacency state |
| `show ip route` | Inspect connected and learned routes |
| `show ip protocols` | Check routing protocol settings |
| `show ip interface brief` | Check interface IPs and status |
| `show ip ospf interface` | Inspect OSPF settings per interface |
| `show ip ospf database` | Inspect the link-state database |

## 11. What I Learned

- Configure IPv4 addresses and subnet masks on Cisco 2911 router interfaces.
- Connect routers and LAN devices with Cisco 2960 switches.
- Enable interfaces using `no shutdown`.
- Configure OSPFv2 using process ID 1 and area 0.
- Use unique router IDs and matching OSPF network statements.
- Verify OSPF neighbor adjacencies and FULL states.
- Recognize OSPF-learned routes marked with `O` in the routing table.
- Confirm remote-LAN reachability using ICMP ping.

## 12. Result

**OSPF was configured successfully.** The routers formed the expected neighbor relationships, R1 learned the remote `192.168.2.0/24` LAN through OSPF, and PC1 reached PC2 with 0% packet loss.
