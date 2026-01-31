# Identifying Speed And Duplex Mismatch 

## Introduction

In this lab, we explore the problems that can happen when network interfaces have mismatched speed or duplex settings. In Packet Tracer, we cannot force a PC NIC to a specific speed or duplex, so for this lab, the focus is on the switch side.

In real-world networks, it’s important to check both ends of a connection to make sure speed and duplex settings match, otherwise performance issues can occur.

In the future, I plan to redo this lab using actual networking hardware to better represent real-world behavior.

## Objective

The goal of this lab is to understand how speed and duplex mismatches happen, how to identify them, and how to fix them

## Equipment And Topology 

- Cisco Packet Tracer
- 1 x Cisco 2960 Switch
- 3 PCs connected via Ethernet
  
<img width="400" height="200" alt="IP-TABLE" src="https://github.com/user-attachments/assets/48aa7485-b9f3-4c8f-baf5-9a94a0f81abc" /> <img width="400" height="200" alt="basic-toplogy" src="https://github.com/user-attachments/assets/1c93071a-6185-41c1-af28-72f2be3d229b" />

**Figure 1&2: network topology and device settings** 

## Checking the interface status 

On a switch, you can check the status of each interface, including speed, duplex, and port type, using commands like:

<img width="500" height="300" alt="show int status" src="https://github.com/user-attachments/assets/ec843140-c834-49ad-a28e-81f4f492f22f" />
**Figure 3: show interfaces command output example** 

In this example, three ports are set to 100 Mbps speed and half-duplex. The PC on the other side (which we can’t show in Packet Tracer) is set to auto-negotiate, so it chooses 100 Mbps and full duplex.

Here’s how auto-negotiation typically works

      if speed 1000mbps > duplex full
      if speed 100mbps > duplex full
      if speed 10mbps > duplex half

Since the PC detects 100 Mbps but sets duplex to full, while the switch is manually set to half, a duplex mismatch occurs. This can cause late collisions and reduced network performance. The tricky part is that the interface may still show “connected,” making the problem harder to spot.

One way to check whether an interface is auto-configured is to look at the speed/duplex column in show interfaces status. If you see an ‘a’ before the value, it means auto-negotiation is enable

Using the command show interfaces status <interface-name> gives more detailed info about each port:

<img width="500" height="303" alt="show-int-status" src="https://github.com/user-attachments/assets/48b7690d-e71c-4ab3-9d4f-9e1a1fbf5e04" />

**Figure 4: show interface status command output example**

You can also use show running-config to see how interfaces are configured:

<img width="225" height="262" alt="running-config-info" src="https://github.com/user-attachments/assets/d4530350-8ec7-409d-8809-e85a6a609ca9" />

**Figure 5: show running-config output example**

Interfaces that explicitly list speed and duplex are usually manually configured. Interfaces without that info are likely auto-negotiated.

## Resolving a mismatch

To fix a mismatch, you can either:

Manually set speed and duplex to the same values on both devices, or

Enable auto-negotiation on both ends so the devices can agree on the correct settings automatically.

This ensures both sides match and avoids network issues like collisions or slow performance.

## Conclusion 

This lab showed how to identify speed and duplex mismatches. The easiest way is using show interfaces status and checking the speed/duplex column for an ‘a’ (which indicates auto).

Other commands like show interfaces <interface> and show running-config provide additional useful info to troubleshoot and confirm the settings. Checking multiple sources helps ensure you don’t miss a mismatch.





