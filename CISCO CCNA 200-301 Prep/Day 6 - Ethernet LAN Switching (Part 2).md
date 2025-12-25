---
---
**Ethernet frame**

* ![[./_resources/Day_6_-_Ethernet_LAN_Switching_(Part_2).resources/image.png]]
* the minimum size of an ethernet frame = header + payload (packet) + trailer = **64 bytes**
	* minus the 18 bytes of the header + trailer, you have the **minimum payload size** of 46 bytes
		* if the payload is less than 46 bytes, **filler bytes of zeros** are added

Devices operating at Layer 2 rather than Layer 3 need to work from MAC addresses rather than IP addresses

* for PC 1 to send packets to PC3 (on another part of the network), you need to use ARP (Address Resolution Protocol)
	* ARP is used to discover the Layer 2 MAC address of a known Layer 3 IP address
	* the process of ARP consists of **two messages**
		* ARP Request
			* PC1 sends the request
			* this request is **broadcast**, meaning it is sent to all hosts on the  network
				* in this case the destination MAC address looks like FFFF.FFFF.FFFF , which is a **broadcast MAC address**
			* when a MAC address is learned via an ARP request this is called a **dynamic MAC address**
		* ARP Reply
			* PC3 sends the reply
			* this is unicast, meaning sent to only one host (the one that sent the request)
			*   a **known unicast frame** is where  you are dealing with a unicast frame and the switch already has the relevant MAC address on file (there is no need to flood or broadcast the MAC address)
	* **ARP Table**
		* ![[./_resources/Day_6_-_Ethernet_LAN_Switching_(Part_2).resources/image.1.png]]
			* in the above, the **physical address** relates to the MAC address (Layer 2) while the **internet address** relates to the IP address (layer 3)
			* **type static**  = default entry
			* **type dynamic**  = learned via ARP

**Ping**

* network utility that is used to test network reachability
* measures round trip time
* uses two messages
	* ICMP Echo Request
	* ICMP Echo Reply
* command is ping \[ip address\]

**Mac Address Table**

* how you find the MAC address on a CISCO IOS device:
	* ![[./_resources/Day_6_-_Ethernet_LAN_Switching_(Part_2).resources/image.2.png]]
* MAC address **aging**:
	* if the switch does not get any traffic from a given MAC address for 5 minutes, it will remove the address from its MAC address table
	* you can manually clear MAC addresses with the command **clear mac address-table dynamic**
	* if you don't want to clear all the dynamic MAC addresses you can use the command **clear mac address-table dynamic address \[the mac address\]**
	* you can clear MAC addresses from a given interface with the command **clear mac address-table dynamic interface \[the interface\]** 

**QUIZ**

1. You perform a packet capture of a 36 byte ping to another computer ;  how do you explain  a string of zeros at the end of the ethernet payload
	* these are padding bytes; the minimum ethernet payload is 46 bytes but only 36 bytes were sent, thus the need for padding bytes

2.  which of these messages is sent to all hosts on the local network?

* ARP request
	* this is meant to find the L2 address (MAC address) of a host; as this address is not yet known, the message must be broadcast to all hosts on the local network

3. which fields are present in the output of the show mac address-table command of a CISCO switch
	* VLAN, MAC address, Type, Ports 

4.  Which types of frames does a switch send out of all interfaces, except the one the frame has received on?

* broadcast, unknown unicast
	* **known unicast** frames are sent to a single host; because the switch already has an entry for the destination in its MAC address table, there is no need to flood the frame out all interfaces
	* broadcast frames have a destination of all FFFF and are sent to all hosts on the local network
	* unknown unicast frames are destined for a single host however the switch doesn't have an entry for the destination in its MAC address table so it must flood the frame
