# Cisco Enterprise Network

A practical Cisco Packet Tracer lab designed to simulate a small enterprise network with VLAN segmentation, Layer 3 routing, Spanning Tree Protocol and dynamic routing with OSPF.

## Project Overview

The network consists of multiple Cisco routers and switches and demonstrates how different network technologies can be combined to provide segmentation, redundancy, routing and basic Layer 2 security.

## Implemented

* VLAN segmentation
* Inter-VLAN routing using Router-on-a-Stick
* 802.1Q trunking
* Spanning Tree Protocol (STP)
* STP root bridge configuration and redundancy
* STP failover testing
* PortFast and BPDU Guard
* Basic switch hardening
* IP addressing and subnetting
* OSPF dynamic routing
* OSPF neighbor relationships
* OSPF route advertisement
* OSPF failover using a third router
* End-to-end connectivity testing

## Network Design

The network is divided into multiple VLANs to separate different network segments.

Each router uses dedicated networks for its VLANs, while the routers are interconnected through separate transit networks.

OSPF is used to dynamically exchange routes between the routers.

A third router provides an alternative path between R1 and R2 in case the direct connection fails.

## Redundancy & Failover

### Spanning Tree Protocol

A redundant Layer 2 topology was created using multiple switches.

STP was configured to control the redundant paths and prevent Layer 2 loops. Root bridge priorities were manually configured to control the preferred topology.

STP failover was tested by disconnecting an active path and verifying that traffic could use the redundant path.

### OSPF

OSPF was configured between R1, R2 and R3 using Area 0.

The direct R1–R2 connection was intentionally disabled to test routing convergence.

After the link failure, OSPF automatically selected the alternative path:

```text
R1 → R3 → R2
```

Connectivity between the networks remained available during the failover.

## Security Features

Access ports were configured with:

```text
PortFast
BPDU Guard
```

BPDU Guard was tested by connecting a switch to a protected access port. The port was automatically placed into an `err-disabled` state after receiving BPDUs.

## Verification

The configuration and functionality were verified using Cisco IOS commands such as:

```text
show vlan brief
show interfaces trunk
show spanning-tree
show ip interface brief
show ip route
show ip route ospf
show ip ospf neighbor
show ip ospf interface brief
show cdp neighbors
```

## Technologies

* Cisco IOS
* Cisco Packet Tracer
* VLAN
* 802.1Q
* STP
* PortFast
* BPDU Guard
* Router-on-a-Stick
* OSPF
* IPv4
* Subnetting

## Project Files

`Cisco-Enterprise-Network-STP-OSPF.pkt` contains the complete Cisco Packet Tracer topology and configuration.

> All credentials and configuration data in this project are fictional and intended for demonstration purposes only.


Screenshots:
<img width="1920" height="1080" alt="Topologie" src="https://github.com/user-attachments/assets/12506e24-2c1e-40e8-9c66-ff6f9fc5ca13" />
<img width="1920" height="1080" alt="BPDU Guard" src="https://github.com/user-attachments/assets/ac40dd4e-25bd-4b18-aacc-32ce7332dda9" />
<img width="1920" height="1080" alt="OSPF Failover" src="https://github.com/user-attachments/assets/768b78b9-e43b-41ca-a7d5-cd7c25691dc8" />

