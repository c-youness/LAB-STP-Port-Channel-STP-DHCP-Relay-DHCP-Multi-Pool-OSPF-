![topologie](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c1df724d-4223-4cee-a475-cacbc74aba17)

![topologie cree vlan](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/3bfe3207-4b18-433a-b3c0-d49e060adfe1)

Switch(config)#vlan 11
================== 
Switch(config-vlan)#name Trade
==================
Switch(config)#vlan 12
==================
Switch(config-vlan)#name Marketing
==================
Switch(config)#vlan 13
==================
Switch(config-vlan)#name IT
==================

![3](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/60f7f1c2-2490-4556-8db3-eefee71081a3)

Switch(config)#vlan 21
==================
Switch(config-vlan)#name SOC_Analyste
==================
Switch(config)#vlan 22
==================
Switch(config-vlan)#name Data_Science
==================
Switch(config)#vlan 23
==================
Switch(config-vlan)#name Cloud_computing
==================
![affichie 4](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/3b82d840-8931-4750-b6a6-7c12cd7b5a3b)

Spanning Tree (PVST)
====================
![Spanning Tree (PVST)](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/ae1ec67f-28d5-4228-b41c-255962cb8f5c)

Switch(config)#spanning-tree vlan 11 root primary 
====================
Switch(config)#spanning-tree vlan 12 root primary 
====================
Switch(config)#spanning-tree vlan 13 root primary 
====================
Switch(config)#spanning-tree vlan 1 root primary
====================
Switch#show spanning-tree
====================
![3](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/105bb53e-aaf9-4a3e-b6d3-b5ef027300f0)


![4](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/58f60ff3-b190-43f1-84a2-4eb8b798ad12)

Switch#show spanning-tree
====================
![5](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/408efd2b-4a19-4380-bf8d-8ae8fd9344f3)


Activation LACP Switch | Multiswitch 
=====================================

![LACP](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/76c6ea12-0ae2-4fe9-b3f2-90573646db6a)


Switch(config)#inter ran f 0/3-4
=====================================
Switch(config-if-range)#channel-group 1 mode active
=====================================

![affichie etherchannel](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/7b9b3996-6e99-4b33-9468-e646ce01c81a)


Multiswitch(config)#inter ran f 0/1-2
=====================================
Multiswitch(config-if-range)#channel-group 1 mode active
=====================================
![multiswitch lacp](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/79782fbe-5d02-4bea-9b1b-8adf810b94ce)



![LACP](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/a4a1e6e3-1481-4142-9aa2-b8a84e006d95)


Switch(config)#inter ran f 0/3-4
=====================================
Switch(config-if-range)#channel-group 1 mode active
=====================================

![affichie ETHERCHANNEL Switch](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/e2f752bb-3d6d-4de4-a5a2-cafbadffddfc)


Multiswitch(config)#inter ran f 0/1-2
=====================================
Multiswitch(config-if-range)#channel-group 1 mode active
=====================================


![affichie ETHERCHANNEL MULTISWITCH](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/317d3b55-1c67-4dc9-b85c-0bf6740a6c9b)

Inter-VLAN Multiswitch
=====================================
Multiswitch(config)#ip routing
=====================================
Multiswitch(config)#int vlan 11
=====================================
Multiswitch(config-if)#ip address 10.10.11.1 255.255.255.0
=====================================
Multiswitch(config-if)#int vlan 12
=====================================
Multiswitch(config-if)#ip  address 10.10.12.1 255.255.255.128
=====================================
Multiswitch(config-if)#int vlan 13
=====================================
Multiswitch(config-if)#ip  address 10.10.13.1 255.255.255.192
=====================================

![show inte vlan multiswtch](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/d710a58d-4ffe-4f61-87ff-3094574aec35)


Multiswitch(config)#ip dhcp pool Admin11
=====================================
Multiswitch(dhcp-config)#network 10.10.11.0 255.255.255.0
=====================================
Multiswitch(dhcp-config)#default-router 10.10.11.1
=====================================
Multiswitch(dhcp-config)#dns-server 1.1.1.1
=====================================
Multiswitch(dhcp-config)#exit
=====================================
Multiswitch(config)#ip dhcp pool Admin12
=====================================
Multiswitch(dhcp-config)#network 10.10.12.0 255.255.255.128
=====================================
Multiswitch(dhcp-config)#default-router 10.10.12.1
=====================================
Multiswitch(dhcp-config)#dns-server 1.1.1.1
=====================================
Multiswitch(dhcp-config)#exit
=====================================
Multiswitch(config)#ip dhcp pool Admin13
=====================================
Multiswitch(dhcp-config)#network 10.10.13.0 255.255.255.192
=====================================
Multiswitch(dhcp-config)#default-router 10.10.13.1
=====================================
Multiswitch(dhcp-config)#dns-server 1.1.1.1
=====================================

Activation Mode Access  
=====================================

![activie mode access](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/91431d2b-4f24-4490-a64c-aa8c22983d93)

Switch1(config)#interface range f 0/5-6
==========================
Switch1(config-if-range)#switchport mode access
==========================
Switch1(config-if-range)#switchport access vlan 11
==========================
![affichie mode acces](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c95251de-8a78-47fb-87ab-b862e1c39198)


Switch(config)#interface range f 0/3-4
==========================
Switch(config-if-range)#switchport mode access
==========================
Switch(config-if-range)#switchport access vlan 11
==========================

