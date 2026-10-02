# $${\color{blue}Basic \space VLAN \space  Segmentation \space Setup \space using \space Cisco \space Packet \space  Tracer  }$$

Ce projet illustre une configuration de base pour la segmentation d'un réseau local (LAN) en utilisant des **VLANs (Virtual Local Area Networks)** sur un switch Cisco 2960 dans Cisco Packet Tracer.

---

##  $${\color{green} Topologie \space du \space Réseau}$$

La topologie se compose d'un switch central connecté à 4 PCs répartis en deux VLANs distincts :

* **VLAN 2 (Sales / Yellow Zone)**
  * **PC1** : `192.168.1.1 /24`
  * **PC2** : `192.168.1.2 /24`
* **VLAN 3 (Marketing / Blue Zone)**
  * **PC3** : `192.168.1.3 /24`
  * **PC0** : `192.168.1.4 /24`

---

##  $${\color{green} Configuration \space du \space Switch \space (CLI)}$$

```diff
enable
configure terminal

! 1. Création des VLANs
vlan 2
 name Sales
exit

vlan 3
 name Marketing
exit

! 2. Assignation des interfaces au VLAN 2
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 2
exit

interface FastEthernet0/2
 switchport mode access
 switchport access vlan 2
exit

! 3. Assignation des interfaces au VLAN 3
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
