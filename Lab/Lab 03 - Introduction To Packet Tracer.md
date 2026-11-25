## Lab 1: Introduction To Packet Tracer

### Getting CISCO Packet Tracer
Please download CISCO Packet Tracer, enroll and complete the CISCO Network Academy. https://www.netacad.com/portal/resources/packet-tracer

### Creating a new topology in packet tracer.
1. Start packet tracer and enter simulation mode

2. Choosing devices and connections

3. Building the topology – Adding Hosts
    1. Single click on the end devices
    2. Single click on the generic host
    3. Move the cursor into topology area. You will notice it turns into a plus “+” sign. Single click in the topology area and it copies the device.

4. Adding a Hub
    1. Select a hub, by clicking once on Hubs and once on a Generic hub
    2. Add the hub by moving the plus sign “+” below PC0 and PC1 and click once.
    3. Connect PC0 to Hub0 by first choosing Connections.
    4. Click once on the Copper Straight-through cable.
    5. Perform the following steps to connect PC0 to Hub0:
        1. Click once on PC0
        2. Choose Fast Ethernet
        3. Drag the cursor to Hub0
        4. Click once on Hub0 and choose Port 0
        5. Notice the green link lights on both the PC0 Ethernet NIC and the Hub0 Port 0 showing that the link is active.

5. Repeat the steps above for PC1 connecting it to Port 1 on Hub0. (The actual hub port you choose does not matter.

### Task 1:
For this task ( Part a, b and c), you have to configure until PCs in the network can ping each other. The network mask used is 255.255.255.0

1. Launch the Packet Tracer, and use it to create and simulate the following networks in (a), (b) and (c).
    1. Assign IP address to both stations, make sure PC1 can ping PC2, viceversa.
    2. Assign IP address to both stations, make sure PC1 can ping PC2, and vice- versa.
    3. Do necessary configuration until PC1, PC2, PC11 and PC22 can ping each other.

You have to configure the fa0/0 with IP address: ***192.168.0.254***.

You have to configure the fa0/1 with IP address: ***192.168.1.254****.

### Task 2:
Use two PCs and one Access Point to create the following wireless network. For each PC, power downs the PC. Change the NIC to wireless NIC. Power on the PC. Connect it to the Access Point.

Configure IP addresses on PC0 and PC1, both PCs should be able to ping each other.

### Task 3: Challenge Lab
Configure a network topology as below and all PCs must be able to ping each other.

<img width="972" height="352" alt="Screenshot 2026-11-25 at 10 19 13 PM" src="https://github.com/user-attachments/assets/8bf83276-4cf4-4a25-b7b7-5f083524e7f9" />

### Reflection questions
#### 1. What are the differences between hub, switch and router setting?
* Hub broadcasts incoming electrical signals out of all ports except the incoming port. It does not inspect MAC or IP addresses, creates a single shared collision domain, and causes more collisions as traffic grows.
* Switch learns device MAC addresses and builds a MAC address table so frames are forwarded only to the destination port. Each port has its own collision domain, improving throughput and reducing collisions within a local network (LAN).
* Router routes packets between different IP networks/subnets using routing tables and IP addresses. Each router interface separates broadcast domains and serves as the default gateway for its connected subnet.

#### 2. What is the purpose of ping?
ping uses ICMP (Internet Control Message Protocol) Echo Request and Echo Reply messages to test whether a target host is reachable over an IP network and to measure round-trip time (latency) and packet loss. It helps confirm basic IP configuration, routing, and network path availability.

#### 3. If you are unable to ping, does it mean that the device is not there?
No. A failed ping can happen even when the device is online and functioning:
* Firewalls, host security settings, or ACLs may drop ICMP echo requests or replies.
* Wrong IP address, subnet mask, missing/incorrect default gateway, or a missing return route on the target or intermediate routers.
* Unplugged cable, powered-off device, or a shutdown interface.

#### 4. Why WiFi differ from Ethernet connection?
WiFi transmits data over radio waves through shared air space, whereas Ethernet sends electrical or optical signals over dedicated copper or fiber cables. Radio signals are more susceptible to physical obstacles, distance, and RF interference from neighboring networks or devices, and require wireless encryption (such as WPA2/WPA3) to protect the airwaves; wired Ethernet is physically contained and generally more consistent in speed and latency. WiFi devices share a wireless channel using contention/scheduling protocols and can roam freely without cables, while Ethernet provides point-to-point or switched wired links with full-duplex dedicated bandwidth.
