## Lab 2: Address Resolution Protocol (ARP)

### Step 1: Finding your IP address and Gateway address
1. Open a command prompt. Please note that you cannot run as an administrator in the lab. Simply type cmd:

2. Find the Ethernet address of the main network interface OR the wireless address (see figure 3) of your computer with the ipconfig command. You will want to know this address for later analysis. On Windows, bring up a command-line shell and type `ipconfig /all`. Among the output will be a section for the main interface of the computer (likely an Ethernet interface) and its Ethernet address. Common names for the interface are “eth0” or “Ethernet adapter”.

3. Find the IP address of the local router or default gateway that your computer uses to reach the rest of the Internet using the netstat / route command. You should be able to use the `netstat -r` command on Windows. Alternatively, you can use the route command (`route print` on Windows). In either case you are looking for the gateway IP address that corresponds to the destination of default or 0.0.0.0.

4. Now run Wireshark by typing “wireshark” in the bottom left search box in Windows

5. You should see the main Wireshark interface. Click on the Ethernet interface to start traffic analysis on that interface.

6. Add a filter of `arp`.

7. When the capture is started, use the `arp` command to clear the default gateway from the ARP cache. Using the command `arp –a` will show you the contents of the ARP cache as a check that you can run `arp`. Go to command prompt and type `arp -a` as shown below. You should see an entry for the IP address of the default gateway.

8. To clear this entry, use the arp command with different arguments (`arp –d` on Windows) as follows. Type `arp -d` in the command prompt.
> [!NOTE]
> This usage of arp will need administrator privileges to run, so you have to run as a privileged user on Windows which is what you should have done in step 1. The command should run without error, but the ARP entry may not appear to be cleared if you check with `arp –a`. This is because your computer will send ARP packets to repopulate this entry as soon as you need to send a packet to a remote IP address, and that can happen very quickly due to background activity on the computer.

9. Now that you have cleared your ARP cache, fetch a remote page with your Web browser. This will cause ARP to find the Ethernet address of the default gateway so that the packets can be sent

10. You will see these packets flowing through your computer by scrolling down in the Wireshark window to the bottom as shown below.

11. These ARP packets will be captured by Wireshark. You might clear the ARP cache and fetch a document a couple of times. Hopefully there will also be other ARP packets sent by other computers on the local network that will be captured. These packets are likely to be present if there are other computers on your local network. In fact, if you have a busy computer and extensive local network then you may capture many ARP packets. The ARP traffic of other computers will be captured when the ARP packets are sent to the broadcast address, since in this case they are destined for all computers including the one on which you are running Wireshark. Because ARP activity happens slowly, you may need to wait up to 30 seconds to observe some of this background ARP traffic.

12. Once you have captured some ARP traffic, stop the capture. You will need the trace, plus the Ethernet address of your computer and the IP address of the default gateway for the next step

### Step 2: Inspect the supplied ARP Trace
1. Close Wireshark.

2. Once Wireshark is closed, open the ARP trace.

3. Now we can look at an ARP exchange. Since there may be many ARP packets in your trace, we’ll first narrow our view to only the ARP packets that are sent directly from or to your computer. Set a display filter for packets with the Ethernet address of your computer which is this case is 00:25:64:d5:10:8b. You can do this by entering an expression in the blank “Filter:” box near the top of the Wireshark window and clicking “Apply” or Enter.

4. Find and select an ARP request for the default gateway and examine its fields. There are two kinds of ARP packets, a request and a reply, and we will look at each one in turn. The Info line for the request will start with “Who has …”. You want to look for one of these packets that asks for the MAC address of the default gateway, e.g., “Who has xx.xx.xx.xx …” where xx.xx.xx.xx is your default gateway. You can click on the + expander or icon for the Address Resolution Protocol block to view the fields:
    * Hardware and Protocol type are set to constants that tell us the hardware is Ethernet and the protocol is IP. This matches the ARP translation from IP to Ethernet address.
    * Hardware and Protocol size are set to 6 and 4, respectively. These are the sizes of Ethernet and IP addresses in bytes.
    * The opcode field tells us that this is a request.
    * Next come the four key fields, the sender MAC (Ethernet) and IP and the target MAC (Ethernet) and IP.

These fields are filled in as much as possible. For a request, the sender knows their MAC and IP address and fills them in. The sender also knows the target IP address – it is the IP address for which an Ethernet address is wanted. But the sender does not know the target MAC address, so it does not fill it in.

5. Next, select an ARP reply and examine its fields. The reply will answer a request and have an Info line of the form “xx.xx.xx.xx is at yy:yy:yy:yy:yy:yy”:
    * The Hardware and Protocol type and sizes are as set as before.
    * The opcode field has a different value that tells us that this is a reply.
    * Next come the four key fields, the sender MAC (Ethernet) and IP and the target MAC (Ethernet) and IP just as before. These fields are reversed from the corresponding request, since the old target is the new sender (and vice versa). The fields should now be all filled in since both computers have supplied their addresses.

### Step 3: Details of ARP over Ethernet
ARP packets are carried in Ethernet frames, and the values of the Ethernet header fields are chosen to support ARP. For instance, you may wonder how an ARP request packet is delivered to the target computer so that it can reply and tell the requestor its MAC address. The answer is that the ARP request is (normally) broadcast at the Ethernet layer so that it is received by all computers on the local network including the target. Look specifically at the destination Ethernet address of a request: it is set to ff:ff:ff:ff:ff:ff, the broadcast address. So, the target receives the request and recognizes that it is the intended recipient of the message; other computers that receive the request know that it is not meant for them. Only the target responds with a reply. However, anyone who receives an ARP packet can learn a mapping from it: the sender MAC and sender IP pair. The ARP header for a request and a reply is 28 bytes for both the request and reply for IPv4.

#### 1. What is the function of ARP in computer networks?
Translate IPv4 addresses into physical MAC addresses so devices can communicate on a local area network (LAN)

#### 2. What opcode is used to indicate a request? What about a reply?
request(1), reply(2)

#### 3. What value is carried on a request for the unknown target MAC address?
00:00:00:00:00:00

#### 4. What Ethernet Type value which indicates that ARP is the higher layer protocol?
0x0806

#### 5. Is the ARP reply broadcast (like the ARP request) or not?
No, ARP requests are broadcast (FF:FF:FF:FF:FF:FF) so all hosts on the local subnet can see them, whereas ARP replies are unicast sent directly back to the requesting host's MAC address.
