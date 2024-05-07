
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
switch(config)#end
================================
switch#show spanning-tree
================================
![sss](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/00ebea2a-3346-4a22-9862-d0288d7865ed)

========================================================================================================================================================

![gggggggggggggg](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/f0345cbb-8654-4cbb-9a9e-fbe10c10b590)

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
![affichie vlan](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/69608280-8544-45b2-b28d-11f2cc83982d)

#show spanning-tree 
-------------------


![spanning](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/8583730f-13cb-4e24-8e2b-ef6218e89ac6)

Same switch EtherChannel (LACP) 
==============================
Switch(config)#inter f 0/4
Switch(config-if)#channel-group 1 mode active

Switch(config)#inter f 0/3
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

![1](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/8bf6b4f4-ae44-44af-a3dc-a80686cece7c)


![99](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/a80ab58c-0a3e-4034-a2d9-44b0fa70f3c4)

MLS-Ring1(config)#int vlan 11
MLS-Ring1(config-if)#ip add 10.10.11.1 255.255.255.0
MLS-Ring1(config-if)#int vlan 12
MLS-Ring1(config-if)#ip add 10.10.12.1 255.255.255.128
MLS-Ring1(config-if)#int vlan 13
MLS-Ring1(config-if)#ip add 10.10.13.1 255.255.255.192

