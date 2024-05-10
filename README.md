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

![affichie vlan](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/b49fc96a-2d09-4aa9-9ce4-1c9004e05d10)

configuration switch EtherChannel (LACP)
=============================
switch(config)#int range f 0/3-4
================================
switch(config-if-range)#channel-group 1 mode active
================================
switch#show etherchannel summary 
================================

![AFFICHIE CHANNEL GROUP](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/99f060e6-a6d8-43b2-972a-d1e372541321)


configuration MultiSwitch
=========================
MultiSwitch(config)#int range f 0/1-2
================================
MultiSwitch(config-if-range)#channel-group 1 mode active
================================
MultiSwitch#show etherchannel summary
================================

![channel group multiswtch](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/0f32f5d6-6ace-43c6-b6fa-96e6c88702e8)


configuration Inter-VLAN
================================

MultiSwitch(config)#ip routing
================================
MultiSwitch(config)#int vlan 11
================================
MultiSwitch(config-if)#ip add 10.10.11.1 255.255.255.0
================================
MultiSwitch(config-if)#int vlan 12
================================
MultiSwitch(config-if)#ip add 10.10.12.1 255.255.255.128
================================
MultiSwitch(config-if)#int vlan 13
================================
MultiSwitch(config-if)#ip add 10.10.13.1 255.255.255.192
================================

configuration DHCP (Ring1-VL11, Ring1-VL12 ,Ring1-VL13)
=======================================================
MultiSwitch(config-if)#ip dhcp pool Ring1-VL11
================================
MultiSwitch(dhcp-config)#network 10.10.11.0 255.255.255.0
================================
MultiSwitch(dhcp-config)#default-router 10.10.11.1
================================
MultiSwitch(dhcp-config)#dns-server 1.1.1.1
================================
MultiSwitch(dhcp-config)#ip dhcp pool Ring1-VL12
================================
MultiSwitch(dhcp-config)#network 10.10.12.0 255.255.255.128
================================
MultiSwitch(dhcp-config)#default-router 10.10.12.1
================================
MultiSwitch(dhcp-config)#dns-server 1.1.1.1
================================
MultiSwitch(dhcp-config)#ip dhcp pool Ring1-VL13
================================
MultiSwitch(dhcp-config)#network 10.10.13.0 255.255.255.192
================================
MultiSwitch(dhcp-config)#default-router 10.10.13.1
================================
MultiSwitch(dhcp-config)#dns-server 1.1.1.1
================================
configuration Port-Channel 
=================

MultiSwitch(config)#interface port-channel 1
=============================
MultiSwitch(config-if)#switchport mode trunk
===================================
MultiSwitch(config-if)#switchport trunk encapsulation dot1q 
===================================
MultiSwitch(config-if)#switchport mode trunk 
===================================
![rrrrr](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/1a500481-792c-48f5-bc2d-deabb83a2fc4)

![ddddd](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/a5fc3b21-eb1b-4f92-ab77-5f70dff5f7bd)







MultiSwitch(config)#interface vlan 11
===================================
MultiSwitch(config-if)#no shutdown 
===================================
MultiSwitch#show ip interface brief 
=========================

![aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/d645beb3-c5ed-48dd-93a5-fd5852e6e990)



MultiSwitch(config)#interface vlan 12
===================================
MultiSwitch(config-if)#no shutdown 
=============================
MultiSwitch(config)#interface vlan 13
===================================
MultiSwitch(config-if)#no shutdown 
=============================
MLS-Ring1(config)#ip dhcp excluded-address 10.10.11.1
=============================
MLS-Ring1(config)#ip dhcp excluded-address 10.10.12.1
=============================
MLS-Ring1(config)#ip dhcp excluded-address 10.10.13.1
=============================
![pinghhhh](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/73046a4f-c36a-40f7-acf1-c736f1c16ff1)



configuration switch Spanning Tree (PVST)
================================
switch(config)#spanning-tree vlan 11 root primary
================================
switch(config)#spanning-tree vlan 12 root primary
================================
switch(config)#spanning-tree vlan 13 root primary
================================
switch(config)#spanning-tree vlan 1 root primary
================================
switch#show spanning-tree
================================
(https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/00ebea2a-3346-4a22-9862-d0288d7865ed)

![yyyyyyyyyy](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/0825c9ca-1502-4d93-b00a-c9077528ebfa)






Switch(config)#inte range fastEthernet 0/5-6
================================
Switch(config-if-range)#switchport mode access
================================
Switch(config-if-range)#switchport access vlan 11
================================
Port-Channel | Mode Trunk
========================
Switch(config)#interface port-channel 1
=====================
Switch(config-if)#switchport mode trunk 
=====================
![ttttttttttttttt](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c64810ba-42e1-4592-a76b-52d82f81140a)


Switch(config)#inte range fastEthernet 0/3-4
===============================
Switch(config-if-range)#switchport mode access
===============================
Switch(config-if-range)#switchport access vlan 11
===============================
Mode Trunk
===========
Switch(config)#interface range fastEthernet 0/1-2
========================
Switch(config-if-range)#switchport mode trunk
=====================

![dddddd](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/7b384619-defa-442a-8860-6c5ed8ec110c)

Switch(config)#inte range fastEthernet 0/3-4
==================
Switch(config-if-range)#switchport mode access
==================
Switch(config-if-range)#switchport access vlan 12
==================
![22222222222222222](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/15528d2d-9344-4676-b752-333740de8dd5)

Switch(config)#inte range fastEthernet 0/3-4
==================
Switch(config-if-range)#switchport mode access
==================
Switch(config-if-range)#switchport access vlan 12
==================
Switch(config)#inte range fastEthernet 0/1-2 
===============
Switch(config-if-range)#switchport mode trunk
===============
![4444444444444](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/c11e9ab8-097c-456f-9b66-87473e16e174)

Switch(config)#inte range fastEthernet 0/3-4
==================
Switch(config-if-range)#switchport mode access
==================
Switch(config-if-range)#switchport access vlan 13
==================
![99999999999999999](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/6c57fb0b-04e0-4c6a-b6f3-7cd2230a88bd)

Switch(config)#inte range fastEthernet 0/3-4
================
Switch(config-if-range)#switchport mode access
================
Switch(config-if-range)#switchport access vlan 13
================
![101010101010110101010](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/e6204d3e-c014-4e19-b2f7-2d8d616d2d08)

Switch(config)#inte range fastEthernet 0/1-2 
================
Switch(config-if-range)#switchport mode trunk
================















Switch(config)#vlan 21
========================
Switch(config-vlan)#name SOC_Analyste
========================
Switch(config)#vlan 22
========================
Switch(config-vlan)#name Data_Science 
========================
Switch(config)#vlan 23
========================
Switch(config-vlan)#name Cloud_computing
========================
![hy](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/9e7826c9-0e36-41d9-a5dc-04368f1aacee)


#show spanning-tree 
-------------------


![spanning](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/8583730f-13cb-4e24-8e2b-ef6218e89ac6)

Same switch EtherChannel (LACP) 
==============================
Switch(config)#inter f 0/4
==============================
Switch(config-if)#channel-group 1 mode active
==============================

Switch(config)#inter f 0/3
==============================
Switch(config-if)#channel-group 1 mode active
==============================

![2](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/6420b615-a643-45d8-bd19-ef7f83ace780)

configuration MultiSwitch (LACP)
===============================
Switch(config)#inter f 0/2
==============================
Switch(config-if)#channel-group 1 mode active
==============================
Switch(config)#inter f 0/1
==============================
Switch(config-if)#channel-group 1 mode active
============================





