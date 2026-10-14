# OSPF Practical — Three-Router Lab

> Cisco Packet Tracer | Cisco 2911 Routers | Cisco 2960 Switches | OSPFv2 | Area 0

## 1. Objective

Configure Open Shortest Path First (OSPF) on three routers so that PC1 can communicate with PC2 across two router-to-router links. Verify OSPF neighbor relationships, learned routes, and end-to-end connectivity.

## 2. Topology

```text
PC1 -- SW1 -- R1 -------- R2 -------- R3 -- SW2 -- PC2
               G0/1       G0/0
              10.0.12.0/30
                          G0/1       G0/0
                         10.0.23.0/30
```

- Routers: Cisco 2911 (R1, R2, R3)
- Switches: Cisco 2960 (SW1, SW2)
- Routing protocol: OSPFv2, process ID 1, area 0
- LAN 1: 192.168.1.0/24
- R1–R2 link: 10.0.12.0/30
- R2–R3 link: 10.0.23.0/30
- LAN 2: 192.168.2.0/24

## 3. IP Addressing Table

| Device | Interface | IP address | Subnet mask | Purpose |
|---|---|---|---|---|
| PC1 | NIC | 192.168.1.10 | 255.255.255.0 | LAN 1 host |
| R1 | G0/0 | 192.168.1.1 | 255.255.255.0 | LAN 1 gateway |
| R1 | G0/1 | 10.0.12.1 | 255.255.255.252 | R1–R2 |
| R2 | G0/0 | 10.0.12.2 | 255.255.255.252 | R1–R2 |
| R2 | G0/1 | 10.0.23.1 | 255.255.255.252 | R2–R3 |
| R3 | G0/0 | 10.0.23.2 | 255.255.255.252 | R2–R3 |
| R3 | G0/1 | 192.168.2.1 | 255.255.255.0 | LAN 2 gateway |
| PC2 | NIC | 192.168.2.10 | 255.255.255.0 | LAN 2 host |

Default gateways:
- PC1: `192.168.1.1`
- PC2: `192.168.2.1`

## 4. Router Configuration

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

## 5. PC Configuration

Configure these values in **Desktop → IP Configuration**.

**PC1**
- IP address: `192.168.1.10`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.1.1`

**PC2**
- IP address: `192.168.2.10`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.2.1`

## 6. Verification Commands

Run these commands from privileged EXEC mode (`R1#`, `R2#`, or `R3#`):

```text
show ip interface brief
show ip ospf neighbor
show ip route
```

### OSPF neighbor verification

The captured output shows these neighbors in the FULL state:

- **R1:** neighbor ID `2.2.2.2`, state `FULL/BDR`, address `10.0.12.2`, interface `GigabitEthernet0/1`.
- **R2:** neighbor ID `1.1.1.1`, state `FULL/DR`, address `10.0.12.1`, interface `GigabitEthernet0/0`.
- **R2:** neighbor ID `3.3.3.3`, state `FULL/BDR`, address `10.0.23.2`, interface `GigabitEthernet0/1`.

### Routing table verification on R1

The captured `show ip route` output includes:
- `C 10.0.12.0/30` — directly connected.
- `O 10.0.23.0/30 [110/2] via 10.0.12.2` — learned through OSPF.
- `C 192.168.1.0/24` — directly connected.
- `O 192.168.2.0/24 [110/3] via 10.0.12.2` — remote LAN learned through OSPF.

## 7. End-to-End Ping Test

From **PC1 → Desktop → Command Prompt**, run:

```text
ping 192.168.2.10
```

**Observed result:** 4 packets sent, 4 received, 0 lost (0% loss). All four replies came from `192.168.2.10`, confirming connectivity from PC1 to PC2 through R1, R2, and R3.

## 8. What I Learned

- Configure IPv4 addresses and subnet masks on Cisco router interfaces.
- Enable router interfaces with `no shutdown`.
- Configure OSPFv2 using process ID 1 and area 0.
- Set unique OSPF router IDs.
- Verify OSPF neighbor adjacencies using `show ip ospf neighbor`.
- Identify OSPF-learned routes marked with `O` in the routing table.
- Test end-to-end connectivity using ICMP ping.
- Understand how dynamic routing shares remote network information between routers.

## 9. Files

- `README.md` — practical overview, addressing, configuration, verification, and learning outcomes.
- `router-configurations.txt` — router CLI configurations.
- `routing-table-r1.txt` — R1 routing table evidence.
- `ospf-neighbors.txt` — OSPF neighbor evidence.
- `ping-test.txt` — PC1-to-PC2 connectivity test output.

> **Note:** The Packet Tracer topology and console outputs were verified from the practical screenshots. Add the original `.pkt` file and screenshots to this folder when uploading those files to the repository.
