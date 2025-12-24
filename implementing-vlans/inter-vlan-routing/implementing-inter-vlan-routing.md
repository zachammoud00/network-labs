# Implementing Inter-Vlan Routing 

## Objective 

To explore how end-devices which reside in different VLANs can send and receive data using a router. This will be a basic configuration 
using separate ports for each corresponding VLAN.  

## Topology 

![image alt](https://github.com/zachammoud00/images/blob/786abc8d0e3a35e358992293fca4ff52421980da/inter-vlan-routing/new_topology.png)

## Equipment 
1 x Cisco Switch
1 x Cisco Router
4 x PC
Ethernet cables 

## Configuration 

![image alt](https://github.com/zachammoud00/images/blob/786abc8d0e3a35e358992293fca4ff52421980da/inter-vlan-routing/switch-router-config.png)

1. Configure each device and port using the set-up in the attached image above.
   
2. In this lab it is important to ensure that the two ports directly connected to the router belong to each VLAN, otherwise the switch will not forward frames across this link,
   otherwise the inter-VLAN routing will not work as the switch will not forward the frame to the router.
   
3. When configuring each of the end devices, ensure the default gateway is set to the ip address of the port on the router which is in the same subnet, this will be directly connected to
   the corresponding port on the switch. Ensure to match VLANs and subnets across all end devices and networking devices, this gives each device a pathway through the network which functions
   correctly. 

4. Testing connectivity - the image below shows PC4 which is in VLAN 20 sending a ping to PC1 in VLAN 10 which demonstrates that this configuration is functioning correctly.

![image alt](https://github.com/zachammoud00/images/blob/786abc8d0e3a35e358992293fca4ff52421980da/inter-vlan-routing/ping%20success.png)
   
## Conclusion 
This lab demonstrated inter-VLAN routing using separate physical router interfaces, allowing devices in different VLANs to communicate at Layer 3. By assignning switch access ports to the correct VLANs 
and connecting each VLAN to a dedicated router interface with a matching IP subnet, traffic was successfully routed between VLAN 10 and VLAN 20. 

This lab reinforced the separation between Layer 2 VLAN segmentation and Layer 3 routing, and proivided a foundational understanding of how VLANs interact with routing devices. 
