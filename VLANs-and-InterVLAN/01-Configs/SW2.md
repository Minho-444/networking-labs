# $${\color{blue}\textbf{Simple VLAN Trunking Setup between 2 Switches} \\ \textbf {Using Cisco Packet Tracer}}$$

This project demonstrates how to configure a **Trunk link** between two Cisco 2960 switches to allow VLAN traffic to pass between network devices.

---

## $${\color{green}\textbf{Network Topology}}$$

The topology consists of two switches connected through a network cable configured as a **Trunk link**:
Switch1 (Blue Zone)
- **$${\color{lightblue} Switch1 \space {Blue \space Zone}}$$**
  - **PC0** connected to `Fa0/1` (VLAN 2)
  - Trunk link to Switch2 through `Fa0/24`

- **$${\color{lightblue} Switch2 \space {yellow \space Zone}}$$**
  - **PC1** connected to `Fa0/1` (VLAN 2)
  - Trunk link to Switch1 through `Fa0/24`

---

## $${\color{green}\textbf{Objective}}$$

The objective of this lab is to:

- Create VLAN 2 on both switches
- Assign PC0 and PC1 to VLAN 2
- Configure the link between the two switches as a **Trunk**
- Allow VLAN 2 traffic to pass between both switches
- Verify connectivity between the two PCs

---

## $${\color{green}\textbf{CLI Configuration}}$$

### $${\color{red}\textbf{1. Switch 1}}$$

```diff
enable
configure terminal

! Create VLAN 2
vlan 2
 name Sales
exit

! Access Port (PC0)
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 2
exit

! Trunk Port (towards Switch2)
interface FastEthernet0/24
 switchport mode trunk
exit

end
write memory
```
###  $${\color{red}2. \space Switch \space 2}$$   

```diff
enable
configure terminal

! Create VLAN 2
vlan 2
 name Sales
exit

! Access Port (PC1)
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 2
exit

! Trunk Port (towards Switch1)
interface FastEthernet0/24
 switchport mode trunk
exit

end
write memory
```

## $${\color{green}\textbf{IP Addressing}}$$

### $${\color{red}\textbf{PC0}}$$

IP Address: `192.168.1.1`  
Subnet Mask: `255.255.255.0`

### $${\color{red}\textbf{PC1}}$$

IP Address: `192.168.1.2`  
Subnet Mask: `255.255.255.0`

Both PCs belong to **VLAN 2** and are therefore part of the same Layer 2 broadcast domain.

---

## $${\color{green}\textbf{Verification}}$$

On both switches, verify the VLAN configuration:

```cisco
show vlan brief
```
### $${\color{red}\textbf{Key Concepts}}$$
  * VLAN 10
  * Access Port
  * Trunk Port
  * 802.1Q VLAN Tagging
  * Layer 2 Switching
  * Broadcast Domain
  * Cisco IOS Configuration
  * Cisco Packet Tracer

###  $${\color{green}\textbf{Files}}$$

  * $${\color{blue} vlan-trunk.pkt}$$ — Cisco Packet Tracer project
  * $${\color{blue} Vlan_Trunk-Topology.png}$$ — Network topology
  * $${\color{blue} Configs/}$$ — Switch configurations
