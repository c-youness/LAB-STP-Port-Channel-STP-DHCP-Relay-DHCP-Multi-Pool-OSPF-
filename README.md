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
Multiswitch(config-if)#exit
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
Multiswitch(config)#ip dhcp excluded-address 10.10.11.1
=====================================
Multiswitch(dhcp-config)#exit
=====================================
![affichiedhcp1](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/46e92c39-bd25-49ba-b440-ba59ce00fbff)

![dhcp11](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/4baee097-621b-4ab4-8195-30eb87b843ee)


Multiswitch(config)#ip dhcp pool Admin12
=====================================
Multiswitch(dhcp-config)#network 10.10.12.0 255.255.255.128
=====================================
Multiswitch(dhcp-config)#default-router 10.10.12.1
=====================================
Multiswitch(dhcp-config)#dns-server 1.1.1.1
=====================================
Multiswitch(config)#ip dhcp excluded-address 10.10.12.1
=====================================
Multiswitch(dhcp-config)#exit
=====================================
![affichie_dhcp_12](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c84fa1fd-146e-4569-b36f-9fa599e9538b)

![dhcp12](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/cc71ef73-0a5b-4959-8ebb-c40f54b7139e)


Multiswitch(config)#ip dhcp pool Admin13
=====================================
Multiswitch(dhcp-config)#network 10.10.13.0 255.255.255.192
=====================================
Multiswitch(dhcp-config)#default-router 10.10.13.1
=====================================
Multiswitch(dhcp-config)#dns-server 1.1.1.1
=====================================
Multiswitch(config)#ip dhcp excluded-address 10.10.13.1
=====================================
![activie_dhcp_13](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/9dcaa171-274e-45c7-a1d6-bbb33dd1f786)

![dhcp13](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/ec6e2739-fa49-4cf7-b6fb-187c23a9284c)


Activation Mode Access (Switch1-Switch2)
========================================

![activie mode access](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/91431d2b-4f24-4490-a64c-aa8c22983d93)

Switch1(config)#interface range f 0/5-6
==========================
Switch1(config-if-range)#switchport mode access
==========================
Switch1(config-if-range)#switchport access vlan 11
==========================
![affichie mode acces](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c95251de-8a78-47fb-87ab-b862e1c39198)


Switch2(config)#interface range f 0/3-4
==========================
Switch2(config-if-range)#switchport mode access
==========================
Switch2(config-if-range)#switchport access vlan 11
==========================
![affiche sw2 mode acc](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/7d640575-2eb0-42e7-a3ae-93fbb950c255)

Activatio nmode trunk
===================
Switch2(config)#interface range f 0/1-2
====================
Switch2(config-if-range)#switchport mode trunk
====================
![mode trunk](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/dce5d747-9044-4749-9a32-9fd0ce68bdcb)

 Activation Mode Access (Switch3 | Switch4)
============================================
![active mode access 3,4](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/50d8f561-9284-4451-bddf-9828d1dc5891)

Switch3(config)#interface range f 0/3-4
=======================
Switch3(config-if-range)#switchport mode access
=======================
Switch3(config-if-range)#switchport access vlan 12
=======================
![affichie mode access switch3](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/f35bb166-65bd-4f9d-9213-9110372d44df)

Switch4(config)#interface range f 0/3-4
=======================
Switch4(config-if-range)#switchport mode access
=======================
Switch4(config-if-range)#switchport access vlan 12
=======================
Activatio nmode trunk
===================
Switch4(config)#interface range f 0/1-2
====================
Switch4(config-if-range)#switchport mode trunk
====================

![mode trunk final](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/a2fcb395-0140-4061-bc01-46d313249a5c)


Activation Mode Access (Switch5 | Switch6)
=======================
![mode access sw5,sw6](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/3c2306f2-01d3-40ce-a59b-6fe9756ed631)

Switch5(config)#interface range f 0/3-4
======================
Switch5(config-if-range)#switchport mode access
======================
Switch5(config-if-range)#switchport access vlan 13
======================

Switch6(config)#interface range f 0/3-4
======================
Switch6(config-if-range)#switchport mode access
======================
Switch6(config-if-range)#switchport access vlan 13
======================
![affichie mode access sw5,sw6](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/ae0ec93d-7874-4212-ba7f-5aef9468b93b)


Activatio nmode trunk
===================
Switch6(config)#interface range f 0/1-2
====================
Switch6(config-if-range)#switchport mode trunk
====================

![mode trunk 01-2](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/f036fd05-b677-4c28-ab6b-2f641f61daf5)


Switch(config)#interface port-channel 1
====================
Switch(config-if)#switchport mode trunk 
====================
![sw1](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/cee1c295-0256-40d4-ba65-c16e8ebc97c6)


Multiswitch(config)#interface port-channel 1
====================
Multiswitch(config-if)#switchport trunk encapsulation dot1q 
====================
Multiswitch(config-if)#switchport mode trunk 
====================
![multiswitch11111](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/07ad29a2-8908-48a0-97b6-ab48d77231cd)




