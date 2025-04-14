# Hotel System Network Design

<img width="1677" alt="Hotel System Network" src="https://github.com/user-attachments/assets/3d0b3331-5c48-42f8-9c69-2f88848913c4" />


## Project Overview

As a part of your end-of-year networking project, you are required to design and implement the Vic Modern Hotel network. The hotel has three floors; on the first floor, there are three departments (Reception, store, and Logistics), on the second floor, there are three departments (Finance, HR, and Sales/Marketing), while the third floor hosts the IT and Admin. Therefore, the following are part of the considerations during the design and implementation;

+ There should be three  routers connecting each floor (all placed in the server room in the IT department).
+ All routers should be connected to each other using a serial DCE cable.
+ The network between the routers should be 10.10.10.0/30,10.10.10.4/30 and 10.10.10.8/30.
+ Each floor is expected to have one switch (placed on the respective floor).
+ Each floor is expected to have WIFI networks connected to  laptops and phones.
+ Each department is expected to have a printer.
+ Each department is expected to be in a different VLAN with the following details;

> 1st Floor;
  1. Reception- VLAN 80, Network of 192.168.8.0/24
  2. Store- VLAN 70, Network of 192.168.7.0/24
  3. Logistics- VLAN 60, Network of 192.168.6.0/24
> 2nd Floor;
  1. Finance- VLAN 50, Network of 192.168.5.0/24
  2. HR- VLAN 40, Network of 192.168.4.0/24
  3. Sales- VLAN 30, Network of 192.168.3.0/24
> 3rd Floor;
  1. Admin- VLAN 20, Network of 192.168.2.0/24
  2. IT- VLAN 10, Network of 192.168.1.0/24

+ Use OSPF as the routing protocol to advertise routes.
+ All devices in the network are expected to obtain IP address dynamically with their respective router configured as the DHCP server.
+ All the devices in the network are expected to communicate with each other.
+ Configure SSH in all the routers for remote login.
+ In the IT department, add PC called Test-PC to port fa0/1 and use it to test remote login.
+ Configure port security to IT-dept switch to allow only Test-PC to access port fa0/1 (use sticky method to obtain mac-address with violation mode of shutdown)
  
---

## Technologies Implemented

1. Creating a network topology using Cisco Packet Tracer.
2. Hierarchical Network Design.
3. Connecting Networking devices with the Correct cabling.
4. Creating VLANs and assigning ports VLAN numbers.
5. Subnetting and IP Addressing.
6. Configuring Inter-VLAN Routing (Router on a stick).
7. Configuring DHCP Server (Router as the DHCP Server).
8. Configuring SSH for secure Remote access.
9. Configuring switchport security or Port-Security on the switches.
10. Configuring WLAN or wireless network (Cisco Access Point).
11. Host Device Configurations.
12. Testing and Verifying Network Communication.

---

### Credits

The network design templates used in this repository are based on resources provided by GurutechNetworks (https://gurutechnetworks.otombenard.com/assetsProject/project3)
