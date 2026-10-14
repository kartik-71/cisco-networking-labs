# DHCP Configuration and Verification Practical

> **Cisco Packet Tracer · Dynamic Host Configuration Protocol · Automatic IPv4 configuration**

## 1. Practical Overview

This practical demonstrates how Dynamic Host Configuration Protocol (DHCP) can provide network settings to client PCs automatically. Instead of manually entering every client's IP configuration, a DHCP server or router configured for DHCP can assign addresses from a configured pool. The lab is documented with a Packet Tracer project, screenshots and a screen-recording video.

## 2. Practical Details

| Item | Details |
|---|---|
| Practical name | Dynamic Host Configuration Protocol (DHCP) Configuration and Verification |
| Software | Cisco Packet Tracer |
| Main topic | Automatic IPv4 configuration using DHCP |
| Supporting concepts | IP addressing, subnet masks, default gateway, DHCP pool and connectivity testing |
| Client verification | PC **Desktop → IP Configuration** and `ipconfig` |
| Router verification | `show ip interface brief`, `show ip dhcp binding`, `show ip dhcp pool` where applicable |

## 3. Objective

To configure and test a DHCP-based network in Cisco Packet Tracer and verify that client PCs receive their network configuration automatically. The practical also aims to check the addressing configuration and test connectivity after DHCP assignment.

## 4. Files Included

| File name | What it is for |
|---|---|
| [`dhcp.pkt`](./dhcp.pkt) | Opens the saved DHCP network topology and device configuration in Cisco Packet Tracer. |
| [`Screen Recording 2026-09-30 202440.mp4`](./Screen%20Recording%202026-09-30%20202440.mp4) | Screen recording of the practical. Use this link to open or download the video. |
| [`Screenshot 2026-09-30 202157.png`](./Screenshot%202026-09-30%20202157.png) | First screenshot captured for the DHCP practical. |
| [`Screenshot 2026-09-30 202208.png`](./Screenshot%202026-09-30%20202208.png) | Second screenshot captured for the DHCP practical. |
| [`Screenshot 2026-09-30 202245.png`](./Screenshot%202026-09-30%20202245.png) | Third screenshot captured for the DHCP practical. |
| [`Screenshot 2026-09-30 202309.png`](./Screenshot%202026-09-30%20202309.png) | Fourth screenshot captured for the DHCP practical. |

## 5. Procedure

### Step 1 — Open Packet Tracer

1. Open Cisco Packet Tracer.
2. Open the existing [`dhcp.pkt`](./dhcp.pkt) project, or create a new workspace if repeating the lab from the beginning.
3. Review the topology and identify the router/server, switch and client PCs.

### Step 2 — Connect the devices

1. Use the **Connections** tool to select the appropriate cables.
2. Connect each PC to the relevant switch.
3. Connect the switch to the device providing network connectivity and DHCP service.
4. Wait for the links to become active and verify that the physical connections match the topology.

### Step 3 — Configure the network and DHCP service

1. Open the relevant router or server configuration.
2. Configure the required interface IP address and subnet mask.
3. Ensure the required interface is enabled.
4. Configure the DHCP service or pool according to the network addressing plan used in the practical.
5. Set the correct network/subnet and, where applicable, the default gateway and DNS settings.
6. Exclude any addresses that must remain reserved for statically configured devices, if required by the lab.

> The exact pool values should match the saved Packet Tracer configuration; they are not assumed in this report.

### Step 4 — Request an address on each PC

1. Open a client PC.
2. Select **Desktop → IP Configuration**.
3. Select **DHCP**.
4. Wait for the client to request and receive its configuration.
5. Check the assigned IPv4 address, subnet mask and default gateway.
6. Repeat for the other client PCs.

### Step 5 — Verify the configuration

On the PC, open **Desktop → Command Prompt** and run:

```text
ipconfig
```

On the router, use the commands applicable to the configuration:

```text
show ip interface brief
show ip dhcp binding
show ip dhcp pool
```

The DHCP commands display address leases and pool information when DHCP is configured on that router. If DHCP is provided by a server instead, inspect the server's DHCP service settings.

### Step 6 — Test connectivity

1. Confirm that the PC has received a valid address.
2. Ping the configured default gateway.
3. If the topology includes other reachable devices, ping the relevant destination IP.
4. If the test fails, check cabling, interface status, the DHCP pool, gateway settings and client address assignment.

## 6. Screenshots and Evidence

### Screenshot 1 — DHCP setup

![DHCP practical screenshot 1](./Screenshot%202026-09-30%20202157.png)

This screenshot is the first visual record of the DHCP practical.

### Screenshot 2 — Configuration evidence

![DHCP practical screenshot 2](./Screenshot%202026-09-30%20202208.png)

Use this screenshot to review the configuration shown in the practical.

### Screenshot 3 — Client or network verification

![DHCP practical screenshot 3](./Screenshot%202026-09-30%20202245.png)

This image provides another stage of the DHCP configuration or verification process.

### Screenshot 4 — Final evidence

![DHCP practical screenshot 4](./Screenshot%202026-09-30%20202309.png)

This is the fourth screenshot included with the practical.

## 7. Practical Demonstration Video

**[▶️ Watch / download the DHCP practical video](./Screen%20Recording%202026-09-30%20202440.mp4)**

The recording is included in this folder. GitHub may not play a large MP4 inline in the code view, but the filename link opens the file page and provides access to the video.

## 8. Main Concepts

### DHCP

DHCP automatically provides client devices with network configuration such as an IPv4 address, subnet mask and default gateway. It reduces the need to manually configure each client and helps avoid address-management mistakes when the pool is configured correctly.

### Address pool and lease

A DHCP pool defines the range and network settings from which client addresses can be assigned. A lease represents the period during which a client may use an assigned address.

### Verification and connectivity

The PC's IP Configuration panel and `ipconfig` help verify client settings. Router DHCP commands, where applicable, help show pool and lease information. Ping can then be used to test reachability.

## 9. What We Learned

- The purpose of DHCP in a computer network.
- How DHCP can automatically assign IPv4 configuration to client PCs.
- How to connect network devices in Cisco Packet Tracer.
- Why the DHCP pool, subnet mask and default gateway must match the network.
- How to set a client to obtain its address using **Desktop → IP Configuration → DHCP**.
- How to inspect client configuration with `ipconfig`.
- How to use router commands to inspect interfaces and DHCP leases/pools where supported.
- How to test connectivity after a client receives its address.
- How to troubleshoot common addressing problems by checking links, interfaces, pool settings and gateways.
- How to present the practical with a Packet Tracer file, screenshots and a video.

## 10. Result

The DHCP practical and its supporting evidence are organized in this folder. Open `dhcp.pkt` to inspect the saved lab, review the screenshots, and use the video link to follow the recorded demonstration. Verify the assigned client addresses in Packet Tracer before concluding that DHCP is working correctly.
