# Basic switch trunking configuration 

## Objective 

To configure a basic trunk port between two switches and test connectivity. 

## Topology 

The topology will be have two switches which are connected through one port, where each switch is directly connected to multiple
devices in different VLANs. 

## Equipment 
Cisco Packet Tracer
Cisco IOS
2 x Cisco Switches 
Crossover ethernet cable
Straight through ethernet cable 

## Configuration 

(For switch 1 and switch 2) 

1. Enter global configuration mode.

  enable 
  configure terminal 

2. Set secret to protect privileged executive and global configuration mode (good practice).

   enable secret cisco

3. access the two ports which will be trunk on switch 1 and switch 2 and set them to trunking, in this case I have chosen GigabitEthernet 0/1 on both switches.

   interface GigabitEthernet 0/1
   switchport moode trunk
   exit

4. Confirm the port is a trunking port afer configuration, you can see the interface details from priveleged executive mode.
   
   show interfaces trunk

   output:

   ![image alt](https://github.com/zachammoud00/images/blob/e374d118bc70a1e24e7d07c1ca73e972c06f4fd0/trunk-int-config.png)

   

### Trunking allows multiple VLANs to be transmitted over a single link between switches. 

## Conclusion 
