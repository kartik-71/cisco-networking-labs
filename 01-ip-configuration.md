# IP Configuration — Cisco Packet Tracer Lab

## Network Overview

This practical uses two routers, two switches, and six PCs.

| Network | Address | Subnet Mask | Purpose |
|---|---|---|---|
| LAN 1 | 192.168.1.0/24 | 255.255.255.0 | Router A / Switch 1 / PCs |
| Serial Link | 10.0.0.0/30 | 255.255.255.252 | Router A ↔ Router B |
| LAN 2 | 192.168.2.0/24 | 255.255.255.0 | Router B / Switch 2 / PCs |

## Router Configuration

| Device | Interface | IP Address | Subnet Mask | Role |
|---|---|---|---|---|
| Router A | Fa0/0 | 192.168.1.1 | 255.255.255.0 | LAN 1 Gateway |
| Router A | S0/1/0 | 10.0.0.1 | 255.255.255.252 | Serial Link |
| Router B | S0/1/0 | 10.0.0.2 | 255.255.255.252 | Serial Link |
| Router B | Fa0/0 | 192.168.2.1 | 255.255.255.0 | LAN 2 Gateway |

## PC Addressing

### LAN 1

| PC | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC0 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.12 | 255.255.255.0 | 192.168.1.1 |

### LAN 2

| PC | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC3 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC4 | 192.168.2.11 | 255.255.255.0 | 192.168.2.1 |
| PC5 | 192.168.2.12 | 255.255.255.0 | 192.168.2.1 |

## Verification Commands

```bash
show ip interface brief
show ip route
ping 10.0.0.2
ping 192.168.2.10
```

## Notes

- LAN 1 uses 192.168.1.0/24.
- LAN 2 uses 192.168.2.0/24.
- The router-to-router serial link uses 10.0.0.0/30.
- Router A provides the default gateway for LAN 1.
- Router B provides the default gateway for LAN 2.
- Connectivity is verified using ping and routing/interface commands.
