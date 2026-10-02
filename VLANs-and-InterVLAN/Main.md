# $${\color{blue}VLAN \space Configuration \space Labs \space using \space Cisco \space Packet \space Tracer}$$

This directory contains a collection of **VLAN configuration labs** developed using **Cisco Packet Tracer**.

The labs cover basic VLAN segmentation and VLAN trunking between Cisco switches.

---

## $${\color{green}Lab \space Overview}$$

### $${\color{red}1. Basic \space VLAN \space Segmentation}$$

A basic VLAN configuration using a Cisco 2960 switch connected to four PCs.

The network is divided into two VLANs:

- **VLAN 2 — Sales**
- **VLAN 3 — Marketing**

Devices within the same VLAN can communicate at Layer 2, while communication between different VLANs is isolated.

**Project file:** `vlan-basic.pkt`

---

### $${\color{red}2. VLAN \space Trunking \space between \space Two \space Switches}$$

A trunking configuration using two Cisco 2960 switches.

Both switches use **VLAN 10**, and the connection between them is configured as a **Trunk link**.

The lab demonstrates how VLAN traffic can be transported between multiple switches.

**Project file:** `vlan-trunk.pkt`

---

## $${\color{green}Network \space Concepts \space Covered}$$

- VLAN creation and configuration
- VLAN segmentation
- Access ports
- Trunk ports
- 802.1Q VLAN tagging
- Layer 2 switching
- Broadcast domains
- Cisco IOS commands
- Cisco Catalyst 2960
- Cisco Packet Tracer

---

## $${\color{green}Repository \space Structure}$$

```text
VLANs-and-InterVLAN/
│
├── README.md
├── Vlan_Trunk-topology.png
├── configuration_vlan.pkt
├── VLANs-Toplogy.png
├── vlan-trunk.pkt
└── configs/
    ├── SW1.txt
    └── SW2.txt
```
##  $${\color{green}Verification \space Commands}$$

The following commands are commonly used to verify VLAN and trunk configurations:

```cisco
show vlan brief
show interfaces trunk
show interfaces status
```
##  $${\color{red}Learning \space Objectives}$$

These labs are designed to build a practical understanding of Cisco switching and VLAN technologies before moving to more advanced networking topics such as:

  * Inter-VLAN Routing
  * Static Routing
  * OSPF
  * DHCP
  * NAT/PAT
  * ACLs
  * Network Security

##  $${\color{red}Tools}$$
  * Cisco Packet Tracer
  * Cisco IOS
  * Cisco Catalyst 2960
