# Static Routing Practical

## Practical Description

In this practical, I worked with Cisco Packet Tracer to understand and configure **static routing** between multiple routers and networks.

The practical involved creating a router topology, connecting the devices, assigning IP addresses to router interfaces and PCs, and adding static routes so that different networks could communicate through the configured next-hop routers.

The practical also included observing the router interfaces and static-route entries in the Cisco Packet Tracer Config tab.

## Topology

The practical uses multiple routers connected through Ethernet links with separate LANs connected to the routers.

The main concepts demonstrated are:

- Router-to-router connectivity
- LAN addressing
- IPv4 addressing
- Static routing
- Next-hop configuration
- Routing between different networks
- Interface configuration and verification
- Redundant network paths

## Static Route Configuration

Static routes were configured by specifying:

- Destination network
- Subnet mask
- Next-hop IP address

The Packet Tracer screenshots show static-route entries configured on the routers.

For example, a static route follows the general format:

```
Network: <destination-network>
Mask: <subnet-mask>
Next Hop: <next-hop-IP>
```

Static routing allows a router to forward packets to a remote network using a manually configured path.

## Router Configuration

The routers were configured through the Cisco Packet Tracer Config/CLI interface.

The practical involved checking the available interfaces and configuring the required router-to-router and LAN connections.

## Verification

The configuration was checked using the router configuration interface and routing information.

The screenshots included with this practical show:

- The Packet Tracer topology
- Static route configuration on a router
- Static route configuration on another router
- The configured router connections

## Video of the Practical

A screen recording of the practical is included in the `media` folder.

## What We Learned

In this practical, I learned:

- How static routing works.
- How routers forward packets to remote networks using a next-hop address.
- How to configure static routes in Cisco Packet Tracer.
- How to identify destination networks and subnet masks.
- How router interfaces are used to connect different networks.
- How to verify routing information from a router.
- How multiple routers can be connected to create different paths between networks.
- How static routes can be used to control the path selected by a router.

## Practical Outcome

The practical helped me understand the difference between directly connected networks and remote networks learned through manually configured static routes.

It also improved my understanding of router interfaces, IPv4 addressing, next-hop routing, and basic network troubleshooting in Cisco Packet Tracer.

---

## Media

The `media` folder contains the screenshots and screen recording associated with this practical.
