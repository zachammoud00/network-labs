# Identifying Speed And Duplex Mismatch 

This lab is focused on identifying the issues that can occur between directly connected network interfaces, such as speed and duplex mismatches. Due to the constraints of packet tracer I cannot configure the PC NIC to force a speed or duplex mode therefore the duplex issues will be on the switch side throughout this lab. However, in the real world it will be important to check the speed and duplex settings on both connected interfaces to identify any speed or duplex mismatches.

In the near future, I will recreate this lab using networking equipment in order to more closely represent real world network behaviours. 

## Objective

The aim of this lab is to explore the different scenarios in which a speed or duplex mismatch errors can occur, and the different ways to identify and correct this issue. 

## Equipment And Topology 

- Cisco Packet tracer
- 1 x 2960 Switch
- 3 Connected PCs via Ethernet

<img width="400" height="200" alt="IP-TABLE" src="https://github.com/user-attachments/assets/48aa7485-b9f3-4c8f-baf5-9a94a0f81abc" /> <img width="400" height="200" alt="basic-toplogy" src="https://github.com/user-attachments/assets/1c93071a-6185-41c1-af28-72f2be3d229b" />

## Checking the interface status 

  - This is done on the switch where you can check the state of the each interface which includes information about speed, duplex, port type etc. On the switch you can run the     following commands to do so:


    <img width="500" height="300" alt="show int status" src="https://github.com/user-attachments/assets/ec843140-c834-49ad-a28e-81f4f492f22f" />

    The highlighted fields are the ones to focus on as it outlines which physical interface is physically connected to the device and information about its speed and duplex.       In this scenario the three highlighted ports have a speed set to 100 and a duplex set to half. As the PC on other side (I can't show due to packet tracing not allowing it)     is set to automatic configuration of speed and duplex. In this particular scenario, the PC will have the settings of speed 100 and duplex full while the switch has been        manually configured to speed 100 and duplex half. This because when speed and duplex is set to auto on one side it sets the duplex according to the speed where the             following applies:

      if speed 1000mbps > duplex full
      if speed 100mbps > duplex full
      if speed 10mbps > duplex half

    The PC will sense the speed of incoming frames and set its own speed to 100 but it will set the duplex to full. So a duplex mismatch occurs between the switch and the PC       which causes late collisions and degraded network performance. This could be difficult to troubleshoot because the interface will show a connected state althought the          theres an issue with the uplinks between the devices.

    This is one way to determine the speed and duplex of connected interfaces on a switch. It gives a hint to whether or not it was automatically set as the speed and duplex
    do not have the 'a' preceding the value as compared to the following roles in the command output. A way of determining this will be discussed in the next section. 










