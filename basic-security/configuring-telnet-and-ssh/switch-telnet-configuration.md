# Configuring Telnet

## Objective

Configure and verify remote management access using Telnet on Cisco IOS device, and explore some security concerns using this method of remote access.

## Topology 

A PC connected to a Cisco switch using a straight-through patch cable in Packet Tracer.

## Configuration 

-- switch configuration -- 

enable
configure terminal
enable secret cisco-switch

-- set the ip address of vlan 1 -- 

interface vlan 1 
ip address 192.168.1.2 255.255.255.0
no shutdown
exit 

-- set the password for the console port -- 

line console 0 
password cisco
exit

-- set the password for remote access lines --

line vty 0 4 
password cisco 
login
transport input telnet
exit

-- configure the ip address on PC1 -- 

192.168.1.3 255.255.255.0 (ensure its in the same subnet as vlan 1 on switch 1) 

-- enter pc command prompt --

telnet 192.168.1.2 

## Conclusion 

Telnet allows remote management of Cisco IOS devices but transmits all data, including authentication credentials, in plain text. This makes Telnet insecure,
as intercepted traffic can easily be read, potentially leading to unauthorised access. For this access, Telnet should be avoided in favour of secure alternatives such 
as SSH. 

