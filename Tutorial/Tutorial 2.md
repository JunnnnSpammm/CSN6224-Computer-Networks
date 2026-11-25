## Part A: Structured

### 1. What are the types of address used in each of the following layer? 
#### Application
Uses names or specific addresses, such as email addresses like `user@example.com`, domain names/URLs like `https://www.example.com`, or service names that identify the specific service or resource.

#### Network
Uses logical addresses, such as IP addresses, IPv4 or IPv6 that uniquely identify a device across an internetwork/different networks.

#### Data-link layer
Uses physical addresses, also known as MAC addresses or link-layer addresses that identify a network interface on a local link/LAN.

### 2. Which of the following data units has an application-layer message plus the header from layer 4? A frame? User datagram? A bit?
User datagram in UDP; or segment in TCP are transport-layer protocol data units.

### 3. What is the role played by network layer during data transmission?
The network layer is responsible for source-to-destination delivery of packets across multiple networks. It add source and destination logical (IP) addresses to packets so they can reach hosts on different networks, determine the best path from the source network to the destination network across intermediate routers. Move packets from an incoming link to the appropriate outgoing link at routers along the path.

### 4. List THREE responsibilities of the data link layer.
1. **Framing:** Grouping the physical layer's bit stream into manageable data units called **frames** and marking frame boundaries.
2. **Physical Addressing:** Adding source and destination MAC (physical) addresses to frames for node-to-node (hop-to-hop) delivery on a local link.
3. **Flow and Error Control:** Managing transmission rate so a fast sender does not overwhelm a slow receiver, and detecting/retransmitting damaged or lost frames.

### 5. Match the following to one of the Internet layers
#### a. Reliable process-to-process data transportation
Transport layer

#### b. Network selection
Network layer

#### c. Routing
Network layer

#### d. Provides user services such as email and file transfer
Application layer

#### e. Transmission of bit stream across physical medium.
Physical layer

#### f. Ensuring reliable transmission of data.
Data-link layer

## Part B: MCQ
1. The process-to-process delivery of the entire message is the responsibility of the ***transport*** layer.

2. The ***physical*** layer is closest to the transmission medium.

3. Mail services are available to users through the ***application*** layer.

4. When independent networks or links are connected to create an internetwork, the connecting devices ***route or switch the packets to their final destination***.
￼
5. The information contained in the data link layer allow for:
    * Framing or dividing the stream of bits into data units called frames.
    * Flow control ensuring that the data rate timing between sender and receiver is maintained.
    * Physical addressing providing node to node information.

6. The physical layer defines the:
    * Characteristics of the interface between the devices and the transmission media.
    * Acceptance of encoded electrical or optical signals.
    * Type of transmission medium.

7. The ***physical*** layer changes streams of bits into electromagnetic signals.

8. When data are transmitted from computing device A to computing device B, the header from A's layer 3 is read by B's ***network*** layer.

9. On the incoming side of the internetwork, as the data packet moves from the lower to the upper layers, headers are ***subtracted***.
