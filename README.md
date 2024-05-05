
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

configuration switch
====================
switch(config)#int range f 0/3-4
================================
switch(config-if-range)#channel-group 1 mode active
================================
switch#show etherchannel summary 
================================

![AFFICHIE CHANNEL GROUP](https://github.com/chalyouness/LAB-STP-Port-Channel-STP-DHCP-Relay-DHCP-Multi-Pool-OSPF-/assets/114768920/99f060e6-a6d8-43b2-972a-d1e372541321)


configuration MultiSwitch
=========================
switch(config)#int range f 0/1-2
================================
switch(config-if-range)#channel-group 1 mode active
================================
switch#show etherchannel summary
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











