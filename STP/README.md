# STP (Spanning Tree Protocol) Practical

## Practical Name
**Basic Practical: STP (Spanning Tree Protocol) — Cisco Packet Tracer**

## Objective
Build a small Ethernet network with redundant links between three switches, configure Spanning Tree Protocol (STP), and verify that PCs can communicate without creating a Layer 2 switching loop.

## Topology
- 3 Cisco 2960 switches: S1, S2, and S3
- 3 PCs: PC1, PC2, and PC3
- Redundant triangular links between the switches
- PC1: `192.168.1.1/24`
- PC2: `192.168.1.2/24`
- PC3: `192.168.1.3/24`

## Configuration Summary
S1 was configured with a lower STP priority so it can become the root bridge for VLAN 1.

```text
enable
configure terminal
hostname S1
spanning-tree mode pvst
spanning-tree vlan 1 priority 4096
end
copy running-config startup-config
```

On S2 and S3, PVST was enabled and the configuration saved:

```text
enable
configure terminal
hostname S2
spanning-tree mode pvst
end
copy running-config startup-config
```

Use the same commands on S3, changing the hostname to `S3`.

## Verification
On each switch, run:

```text
show spanning-tree
show spanning-tree vlan 1
```

S1 should be elected the root bridge. STP should place one end of the redundant S2–S3 link into an alternate/blocking state to prevent a Layer 2 loop. The exact switch port that blocks can vary based on bridge IDs and port costs.

## Ping Test Results
The supplied PC1 command prompt shows successful tests:
- `ping 192.168.1.2` — PC1 to PC2
- `ping 192.168.1.3` — PC1 to PC3

Both tests show **4 packets sent, 4 received, 0% packet loss**.

![PC1 ping results](./STP-Ping-Results.svg)

> The terminal visual is a recreated, readable version of the supplied ping screenshot.

## What I Learned
- STP prevents Layer 2 loops when redundant switch links exist.
- The switch with the lowest bridge priority is preferred as the root bridge.
- STP uses root, designated, and alternate port roles to maintain a loop-free topology.
- Redundant links can remain available while STP blocks one path to avoid loops.
- The `show spanning-tree vlan 1` command helps verify the root bridge and port states.
- Successful ping tests confirm end-to-end IP connectivity between the PCs.

## Files
- [PC1 ping results](./STP-Ping-Results.svg)
- The original Packet Tracer project (`stp.pkt`) was supplied in chat but has not been uploaded to this repository in this commit.
