
# Cisco Switch SSH configuration

## Objective 
Configure SSH on Cisco switch in packet tracer and remotely access the switch using a connected PC. 

## Topology
A single Cisco switch directly connected to a PC using a straight-through patch cable. 

## Configuration 

(the following is completed in global configuration mode)

enable 
configure terminal 
enable secret Cisco 
hostname SW1 
ip domain name example.com
crypto key generate rsa
1024
ip ssh version 2 

username zac password cisco 

line vty 0 15
password cisco
login local
transport input ssh
exit

interface vlan 1 
ip address 192.168.1.2 255.255.255.0
no shutdown 
exit 

-- configure ip on PC1 -- 
(ensure PC1 is in the same subnet as VLAN 1) 
192.168.1.3 
255.255.255.0 

(access the command prompt on PC1) 
ssh -l zac 192.168.1.2 

## Conclusion
SSH should always be used over Telnet for remote management because it encrypts transmitted data, preventing credentials and commands from being read if traffic is intercepted.

SSH on Cisco IOS requires a configured hostname, domain name, local user credentials, and RSA keys. SSHv2 requires a minimum RSA key size of 768 bits, though larger key sizes such as 1024 bits provide stronger encryption and are recommended.

For improved security, Telnet should be disabled and only SSH permitted on the VTY lines.
