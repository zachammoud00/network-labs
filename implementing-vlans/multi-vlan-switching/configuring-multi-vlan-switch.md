# Basic multi VLAN Switching

## Objective

Configure a single switch connected to multiple devices using several VLANs. 

## Topology

A single Cisco switch directly connected to a several PCs using straight-through patch cables.

![image alt](https://github.com/zachammoud00/network-labs/blob/b75e69895ff95b70170a766ba1873c99f436ce89/implementing-vlans/multi-vlan-switching/topology.png)

## Configuration

### enter global configuration mode 

enable 

configure terminal 

### create VLAN 2 and set the name (repeat for all relevant vlans- i will not add all commands but see device configuration file for more details). 

vlan 2 

name accounting-dept 

exit 

### assign interfaces with the relevant VLANs (repeat for all interfaces associated with specific VLANs).

interface range FastEthernet 0/1-3

(assign these ports as access ports)

switchport mode access 

(assign these ports to vlan 2, this means they can only interact with other devices within the same VLAN)

switchport access vlan 2 

### configure each specific device (see device configuration file).

![image alt](https://github.com/zachammoud00/network-labs/blob/5e0ea8b34c6898fb8bf105a87f25468a039e7c33/implementing-vlans/multi-vlan-switching/device-config.png)

### test connectivity with device within the same VLAN
source: 192.168.2.2 (VLAN 2)

destination: 192.168.2.3 (VLAN 2) 

ping 192.168.2.3

![image alt](https://github.com/zachammoud00/network-labs/blob/2c78f1e46b5c324edb593c0cd8293547517b8126/implementing-vlans/multi-vlan-switching/1.0.png)

### test connectivity with device in a different VLAN 
source: 192.168.2.2 (VLAN 2)

destination: 192.168.3.3 (VLAN 3)

ping 192.168.3.3

![image alt](https://github.com/zachammoud00/network-labs/blob/0148186c1d0bbb5a94b63938e74e7a5ad7ea1794/implementing-vlans/multi-vlan-switching/2.0.png)

## Conclusion

This was a basic multi VLAN configuration which used only 1 switch device, there were 3 VLAN's in total:

1. VLAN 2: 3 devices
2. VLAN 3: 3 devices
3. VLAN 4: 2 devices

The devices in each VLAN were only able to connect with devices within the same VLAN as inter-VLAN routing was not set up in this lab.
This lab tries to demosntrate the logical grouping of devices residing on a switch using different VLAN's, this can be an advantage for several reasons
ranging from increased security to device performance. In terms of security each device is only able to transmit frames to other devices within the same broadcast domain
meaning that the risk of an unathorised device in another VLAN receiving the frame is minimised. For device performance by segmenting the network, when a swtich does not have a destination MAC address
for a frame it receives, it will only flood devices on ports with an unknown unicast frame within the same VLAN, rather than all ports if VLANs were not configured. For a small network setup similar to this lab, the 
increase in performance will be negligible but in large enterprise networks there will be a greater gain. 
