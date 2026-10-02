# $${\color{blue}Basic \space VLAN \space  Segmentation \space Setup \space using \space Cisco \space Packet \space  Tracer  }$$

This project demonstrates a basic **LAN segmentation** configuration using **VLANs (Virtual Local Area Networks)** on a Cisco Catalyst 2960 switch in Cisco Packet Tracer.

## $${\color{green} Network \space Topology}$$

The topology consists of one central switch connected to four PCs divided into two separate VLANs.

<img width="832" height="462" alt="Screenshot 2026-10-02 135852" src="https://github.com/user-attachments/assets/8b826bcf-507e-4153-828f-85c98a7ce381" />


### $${\color{yellow} VLAN \space 2 \space — \space Sales  / Yellow \space Zone}$$

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC1 | `192.168.1.1` | `255.255.255.0` |
| PC2 | `192.168.1.2` | `255.255.255.0` |

### $${\color{blue} VLAN \space 2 \space — \space Marketing  / Blue \space Zone}$$

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC3 | `192.168.1.3` | `255.255.255.0` |
| PC0 | `192.168.1.4` | `255.255.255.0` |

The four PCs use the same IP subnet but are separated into different **Layer 2 broadcast domains** through VLAN segmentation.

> No default gateway is required for this basic Layer 2 VLAN lab because no inter-VLAN routing is configured.

## $${\color{green} \textbf {Switch Configuration}}$$

```diff
enable
configure terminal

! 1. Create VLANs

vlan 2
 name Sales
exit

vlan 3
 name Marketing
exit

! 2. Assign interfaces to VLAN 2

interface FastEthernet0/1
 switchport mode access
 switchport access vlan 2
exit

interface FastEthernet0/2
 switchport mode access
 switchport access vlan 2
exit

! 3. Assign interfaces to VLAN 3

interface FastEthernet0/3
 switchport mode access
 switchport access vlan 3
exit

interface FastEthernet0/4
 switchport mode access
 switchport access vlan 3
exit

end
write memory
```
## $${\color{green} \textbf {Port Assignment}}$$
| Switch Port | Connected Device | VLAN | Department |
|---|---|---|---|
| FastEthernet0/1 | PC1 | VLAN 2 | Sales |
| FastEthernet0/2 | PC2 | VLAN 2 | Sales |
| FastEthernet0/3 | PC3 | VLAN 3 | Marketing |
| FastEthernet0/4 | PC0 | VLAN 3 | Marketing |

## $${\color{green} \textbf {IP Addressing}}$$

###  $${\color{red} \textbf {VLAN 2 — Sales}}$$

#### $${\color{lightblue} \textbf {PC1}}$$


```text
IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0
Default Gateway: Not required
```

#### $${\color{lightblue} \textbf {PC2}}$$

```text
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
Default Gateway: Not required
```

###  $${\color{red} \textbf {VLAN 3 — Marketing}}$$

#### $${\color{lightblue} \textbf {PC3}}$$

```text
IP Address: 192.168.1.3
Subnet Mask: 255.255.255.0
Default Gateway: Not required
```

#### $${\color{lightblue} \textbf {PC0}}$$

```text
IP Address: 192.168.1.4
Subnet Mask: 255.255.255.0
Default Gateway: Not required
```

## $${\color{green} \textbf {IP Verification}}$$

###  $${\color{red} \textbf {Verify VLAN Creation and Port Assignments}}$$

Run the following command on the switch:

```cisco
show vlan brief
```

This command displays the VLANs created on the switch and the interfaces assigned to each VLAN.
    
###  $${\color{red} \textbf {Test Connectivity Within the Same VLAN}}$$
From PC1, test connectivity with PC2:

```text
PC1> ping 192.168.1.2
```

This ping should succeed because PC1 and PC2 belong to the same VLAN.

From PC3, test connectivity with PC0:

```text
PC3> ping 192.168.1.4
```

This ping should also succeed because PC3 and PC0 belong to the same VLAN.

###  $${\color{red} \textbf {Test Connectivity Between Different VLANs}}$$


From PC1, test connectivity with PC3:

```text
PC1> ping 192.168.1.3
```

This ping should fail because PC1 belongs to VLAN 2, while PC3 belongs to VLAN 3.

VLAN 2 and VLAN 3 are separate Layer 2 broadcast domains, and no Layer 3 routing has been configured between them.

## $${\color{green} Key \space Concepts}$$

- VLAN 2
- VLAN 3
- VLAN Segmentation
- Access Ports
- Layer 2 Switching
- Broadcast Domains
- Cisco IOS Configuration
- Cisco Catalyst 2960
- Cisco Packet Tracer
- Network Isolation
- Basic LAN Segmentation

## $${\color{green}  Project \space Files}$$

```text
basic-vlan.pkt          Cisco Packet Tracer project
topology.png            Network topology image
configs/SW1.txt         Switch configuration
README.md               Project documentation
```

## $${\color{green} Result  }$$

The network was successfully segmented into two VLANs:

- PC1 and PC2 can communicate within VLAN 2.
- PC3 and PC0 can communicate within VLAN 3.
- Communication between VLAN 2 and VLAN 3 is isolated.
- Inter-VLAN communication is unavailable because no Layer 3 routing has been configured.
