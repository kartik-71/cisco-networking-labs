# DHCP Configuration Practical

## Practical Name

**Dynamic Host Configuration Protocol (DHCP) Configuration and Verification using Cisco Packet Tracer**

---

## Objective

To configure and test DHCP in a Cisco Packet Tracer network and verify that connected PCs can obtain their network configuration automatically.

---

## Software Used

- Cisco Packet Tracer
- Cisco IOS command-line interface
- PC Command Prompt in Packet Tracer

---

## Practical Files

| File | Description |
|---|---|
| `dhcp.pkt` | Cisco Packet Tracer practical file |
| `Screen Recording 2026-09-30 202440.mp4` | Practical demonstration video |
| `Screenshot 2026-09-30 202157.png` | Practical screenshot |
| `Screenshot 2026-09-30 202208.png` | Practical screenshot |
| `Screenshot 2026-09-30 202245.png` | Practical screenshot |
| `Screenshot 2026-09-30 202309.png` | Practical screenshot |

---

## Procedure

### 1. Open Cisco Packet Tracer

1. Open **Cisco Packet Tracer**.
2. Start a new workspace.
3. Add the required network devices and PCs.
4. Arrange the devices so the network topology is easy to configure and understand.

### 2. Connect the Devices

1. Select the appropriate cable from the **Connections** section.
2. Connect the network devices and PCs.
3. Wait for the interfaces/links to become active.
4. Check that the physical connections are correct before starting the configuration.

### 3. Configure the Network

1. Open the required router/device.
2. Go to the **CLI**.
3. Configure the required interface IP addressing.
4. Make sure the interface is enabled.
5. Configure the DHCP service/pool according to the network used in the practical.

### 4. Configure the PCs for DHCP

1. Open a PC.
2. Select **Desktop**.
3. Open **IP Configuration**.
4. Select **DHCP** instead of entering the IP address manually.
5. Check whether the PC receives its network configuration automatically.
6. Repeat this for the required PCs.

### 5. Verify the DHCP Configuration

Use the Packet Tracer CLI and PC command prompt to verify the configuration.

Useful verification commands include:

```text
show ip interface brief
```

and, where applicable:

```text
show ip dhcp binding
show ip dhcp pool
```

On a PC, the assigned configuration can also be checked from:

**Desktop → Command Prompt**

```text
ipconfig
```

### 6. Test Connectivity

After the PCs receive their IP configuration:

1. Open the PC Command Prompt.
2. Check the assigned IP address.
3. Test connectivity using `ping`.
4. Confirm that the expected devices can communicate successfully.

Example:

```text
ping <destination-ip>
```

---

## Screenshots

### Screenshot 1

![DHCP Practical Screenshot 1](./Screenshot%202026-09-30%20202157.png)

### Screenshot 2

![DHCP Practical Screenshot 2](./Screenshot%202026-09-30%20202208.png)

### Screenshot 3

![DHCP Practical Screenshot 3](./Screenshot%202026-09-30%20202245.png)

### Screenshot 4

![DHCP Practical Screenshot 4](./Screenshot%202026-09-30%20202309.png)

---

## Practical Demonstration Video

The complete practical demonstration is available here:

**[▶️ Watch / Download the Practical Video](./Screen%20Recording%202026-09-30%20202440.mp4)**

> GitHub may not preview a large MP4 directly in the repository file viewer. The link above opens the video file.

---

## What We Learned

From this practical, we learned:

- The purpose of **DHCP** in a computer network.
- How DHCP can automatically provide network configuration to client PCs.
- How to configure and work with a DHCP-based network in **Cisco Packet Tracer**.
- How to configure network interfaces before testing connectivity.
- How to configure PCs to obtain their IP configuration automatically.
- How to verify assigned IP configuration from a PC.
- How to use Cisco IOS verification commands to check the network configuration.
- How to test connectivity using the `ping` command.
- How to troubleshoot basic connectivity problems by checking the configuration and connections.
- How to document a networking practical using screenshots, a Packet Tracer file, and a demonstration video.

---

## Practical Resources

- **Packet Tracer File:** [dhcp.pkt](./dhcp.pkt)
- **Demonstration Video:** [Screen Recording 2026-09-30 202440.mp4](./Screen%20Recording%202026-09-30%20202440.mp4)

---

## Result

The DHCP practical was configured and tested in Cisco Packet Tracer, with the configuration documented using screenshots, the Packet Tracer file, and a demonstration video.
