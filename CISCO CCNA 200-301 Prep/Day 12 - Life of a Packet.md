---
---
**ARP Process**

* ![[./_resources/Day_12_-_Life_of_a_Packet.resources/image.1.png]]
* ARP request = broadcast
* ARP reply = Unicast

![[./_resources/Day_12_-_Life_of_a_Packet.resources/image.png]]

* the above network topology will be used for the below quiz

**QUIZ**

1. PC4 sends  a packet to PC1.  what is the **destination MAC address** when it is sent from **PC4's** network interface?
	* fffe
		* to send a packet to PC1, which is in a remote network, PC4 must send a packet to its default gateway, R4, first
2. PC4 sends  a packet to PC1, what is the **source MAC address** when it is received on **R1's Gi0/0 interface?**
	* **cccc**
		* when R2 sends a packet to R1, it encapsulates the packet with a header with R2's own MAC address as the source address

3. PC4 sends  a packet to PC1.  what is the **source MAC address** when sent from **SW1's Gi0/1 interface**?
	* aaaa
		* SW1 does  not alter the frame to use its own MAC, it simply forwards the frame out of the correct interface or floods the frame if it doesn't know the destination

4. PC4 sends  a packet to PC1..  what is the **destination IP address** when it's sent from **R4's Gi0/1 interface?**
	* 192.168.1.1
		* while routers modify the source and destination MAC address of packets, they don't modify the original packet itself so the destination IP address won't change

5. PC4 sends  a packet to PC1.  what is the **source IP address** when it is received on **R1's Gi0/0 interface**
	* **192.168.4.1**
		* the original source IP is not modified on its journey
