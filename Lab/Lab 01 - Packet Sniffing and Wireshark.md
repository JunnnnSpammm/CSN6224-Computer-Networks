## Lab 1: Packet Sniffing and Wireshark

### Getting Wireshark
Wireshark can be downloaded from here: https://www.wireshark.org/download.html

### Starting Wireshark
When you run the Wireshark program, the Wireshark graphic user interface will be shown as Figure 5. Currently, the program is not capturing the packets.

Then, you need to choose an interface. If you are running the Wireshark on your laptop, you need to select WiFi interface. If you are at a desktop, you need to select the Ethernet interface being used. Note that there could be multiple interfaces. In general, you can select any interface but that does not mean that traffic will flow through that interface. The network interfaces (i.e., the physical connections) that your computer has to the network are shown. The attached Figure 6 was taken from my computer.

After you select the interface, you can click start to capture the packets as shown in Figure 7.

The Wireshark interface has five major components:

1. Command menus are standard pulldown menus located at the top of the window. Of interest to us now is the File and Capture menus. The File menu allows you to save captured packet data or open a file containing previously captured packet data, and exit the Wireshark application. The Capture menu allows you to begin packet capture.

2. The packet-listing window displays a one-line summary for each packet captured, including the packet number (assigned by Wireshark; this is not a packet number contained in any protocol’s header), the time at which the packet was captured, the packet’s source and destination addresses, the protocol type, and protocol-specific information contained in the packet. The packet listing can be sorted according to any of these categories by clicking on a column name. The protocol type field lists the highest level protocol that sent or received this packet, i.e., the protocol that is the source or ultimate sink for this packet.

3. The packet-header details window provides details about the packet selected (highlighted) in the packet-listing window. (To select a packet in the packet-listing window, place the cursor over the packet’s one-line summary in the packet-listing window and click with the left mouse button.). These details include information about the Ethernet frame and IP datagram that contains this packet. The amount of Ethernet and IP-layer detail displayed can be expanded or minimized by clicking on the right pointing or down-pointing arrowhead to the left of the Ethernet frame or IP datagram line in the packet details window. If the packet has been carried over TCP or UDP, TCP or UDP details will also be displayed, which can similarly be expanded or minimized. Finally, details about the highest-level protocol that sent or received this packet are also provided.

4. The packet-contents window displays the entire contents of the captured frame, in both ASCII and hexadecimal format.

5. Towards the top of the Wireshark graphical user interface, is the packet display filter field, into which a protocol name or other information can be entered in order to filter the information displayed in the packet-listing window (and hence the packet-header and packet-contents windows). In the example below, we’ll use the packet-display filter field to have Wireshark hide (not display) packets except those that correspond to HTTP messages.

### Capturing Packets
After downloading and installing Wireshark, you can launch it and click the name of an interface under Interface List to start capturing packets on that interface. For example, if you want to capture traffic on the wireless network, click your wireless interface.

### Test Run
Do the following steps:
1. Start up the Wireshark program (select an interface and press start to capture packets).

2. Start up your favorite browser (e.g. Chrome).

3. In your browser, go to MMU homepage by typing www.mmu.edu.my.

4. After your browser has displayed the http://www.mmu.edu.my page, stop Wireshark packet capture by selecting stop in the Wireshark capture window. This will cause the Wireshark capture window to disappear and the main Wireshark window to display all packets captured since you began packet capture see image below:

5. Color Coding: You’ll probably see packets highlighted in green, blue, and black. Wireshark uses colors to help you identify the types of traffic at a glance. By default, green is TCP traffic, dark blue is DNS traffic, light blue is UDP traffic, and black identifies TCP packets with problems — for example, they could have been delivered out-of-order.

6. You now have live packet data that contains all protocol messages exchanged between your computer and other network entities! However, as you will notice the HTTP messages are not clearly shown because there are many other packets included in the packet capture. Even though the only action you took was to open your browser, there are many other programs in your computer that communicate via the network in the background. To filter the connections to the ones we want to focus on, we have to use the filtering functionality of Wireshark by typing “http” in the filtering field as shown below. Notice that we now view only the packets that are of protocol HTTP. However, we also still do not have the exact communication we want to focus on because using HTTP as a filter is not descriptive enough to allow us to find
our connection to http://www.mmu.edu.my. We need to be more precise if we want to capture the correct set of packets.

7. To further filter packets in Wireshark, we need to use a more precise filter. By setting the http.host==www.mmu.edu.my, we are restricting the view to packets that have as an http host the www.wayne.edu website. Notice that we need two equal signs to perform the match “==” not just one.

8. Now, we can try another protocol. Let’s use Domain Name System (DNS) protocol as an example here.
￼
9. Let’s try now to find out what are those packets contain by following one of the conversations (also called network flows), select one of the packets and press the right mouse button (if you are on a Mac use the command button and click), you should see something similar to the screen below: Click on Follow UDP Stream, and then you will see following screen.
￼
10. If we close this window and change the filter back to “http.host==www.mmu.edu.my” and then follow a packet from the list of packets that match that filter, we should get the something similar to the following screens. Note that we click on Follow TCP Stream this time.
￼
### Questions for the Lab
#### 1. Carefully read the lab instructions and finish all tasks above.

#### 2. If a packet is highlighted by black, what does it mean for the packet?
In network analyzers like Wireshark, a packet highlighted in black (typically with red text on a black background) indicates a TCP error or network anomaly. Common causes include: Out-of-order packets, Retransmissions, Duplicate ACKs, Window updates or segment-related issues

#### 3. What is the filter command for listing all outgoing http traffic?
```
http
```

#### 4. Why does DNS use Follow UDP Stream while HTTP use Follow TCP Stream?
* DNS uses UDP because name resolution needs to be extremely fast and lightweight. Most DNS queries and responses consist of a single small request packet and a single response packet that easily fit within a single UDP datagram. Because UDP require no handshake, it introduces minimal latency and overhead, allowing domain name lookups to happen instantly.

* HTTP uses TCP because web browsing requires reliable, ordered, and error-free delivery of data. Web pages, scripts, images, and other resources consist of large amounts of data stream segments. If a packet is lost or arrives out of order, TCP handles retransmission and reassembly automatically to ensure the web page is not corrupted or broken.

### Your final task
* Upon completing the experiment, present your results and respond the questions above to the lab instructors.
*  No formal submission is required for this experiment, and it will not be graded.
￼
