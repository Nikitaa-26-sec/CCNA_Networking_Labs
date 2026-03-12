# CCNA_Networking_Labs
CCNA networking labs built using Cisco Packet Tracer demonstrating VLAN configuration, inter-VLAN routing (ROAS), trunking, and multi-router packet flow. These simulations showcase practical routing and switching concepts essential for network engineering and cybersecurity.


# Inter-VLAN Routing using Router-on-a-Stick

## Objective
Enable communication between devices in different VLANs using a router and a trunk link.

## Devices Used
- Cisco 2811 Router
- Cisco 2960 Switch
- 2 PCs

## VLANs
VLAN 10 – Network A  
VLAN 20 – Network B

## Network Design
Two PCs belong to different VLANs.  
The router performs routing between VLANs using subinterfaces.

## Switch Configuration

Create VLANs

Switch(config)# vlan 10
Switch(config)# vlan 20

Assign VLANs

Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10

Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20

Configure trunk to router

Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk

## Router Configuration

Router(config)# interface fa0/0
Router(config-if)# no shutdown

Router(config)# interface fa0/0.10
Router(config-subif)# encapsulation dot1Q 10

Router(config)# interface fa0/0.20
Router(config-subif)# encapsulation dot1Q 20

# VLAN Configuration with Two Switches

## Objective
To configure VLANs on two switches and allow devices in the same VLAN to communicate across switches using trunking.

## Devices Used
- 2 Cisco 2960 Switches
- 8 PCs
- Ethernet cables

## VLANs Created
VLAN 10 – Sales  
VLAN 20 – HR

## Network Design
Each switch connects multiple PCs.  
The two switches are connected using a trunk link to allow VLAN traffic between them.

## Configuration Steps

### Switch Configuration

Create VLANs

Switch(config)# vlan 10
Switch(config-vlan)# name SALES

Switch(config)# vlan 20
Switch(config-vlan)# name HR

Assign PCs to VLANs

Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10

Switch(config)# interface fa0/2
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 20

Configure trunk between switches

Switch(config)# interface fa0/24
Switch(config-if)# switchport mode trunk

## Result
Devices within the same VLAN can communicate across both switches.


 # Packet Flow through Three Routers

## Objective
Demonstrate how packets travel across multiple routers between two networks.

## Devices Used
- 3 Cisco 2811 Routers
- 2 PCs

## Network Design
PC0 connects to Router0.  
Router0 connects to Router1.  
Router1 connects to Router4.  
Router4 connects to PC1.

The packet travels across all routers to reach the destination.

## Concepts Demonstrated
- Routing
- Packet forwarding
- Multi-hop communication

## Routing Configuration Example

Router(config)# ip route 192.168.2.0 255.255.255.0 next-hop-ip

## Result
Packets successfully travel from PC0 to PC1 through the routers.

## Result
Devices from VLAN 10 and VLAN 20 can communicate through the router.
