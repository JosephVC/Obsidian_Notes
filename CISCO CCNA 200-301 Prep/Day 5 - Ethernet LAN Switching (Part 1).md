---
---
There are 5 LANs in the below pictures

* LANs 3 and 4 are considered separate, as they connect separately to the router leading to the internet
* ![[./_resources/Day_5_-_Ethernet_LAN_Switching_(Part_1).resources/image.png]]

**Ethernet frame**

* ![[./_resources/Day_5_-_Ethernet_LAN_Switching_(Part_1).resources/image.1.png]]
	* **Preamble**
		* length: 7 bytes
		* binary code
		* allows devices to synchronize their receiver clocks
	* **SFD (Start Frame Delimiter)**
		* length: 1 byte
		* marks the end of the preamble, at the beginning of the frame
	* **Destination & Source**
		* Indicate the devices sending and receiving the frame
		* consist of the destination and source MAC address
			* **MAC**: Media Access Control
				* 6 byte  address of a physical device
				* separate from a logical address like an IP address
				* assigned during a device's construction
				* can also be called the BIA (Burned In Address)
				* is globally unique, as no two devices should have the same MAC addresses
				* the first three bytes of a MAC address is the **OUI (Organizationally Unique Identifier)**
				* the last three bytes are unique to the device itself
				* Written as 12 hexadecimal characters
					* in the **decimal** system, you get ten possible digits from 0 values of 1 to 9 values of 1; when you get to the 10s column you start with 10 (**one value of 10 and zero values of one), then 11 (one value of 10 and one value of 1)**
					* in hexadecimal, you get **16 possible digits**
						* the first ten are the same as in decimal (0-9) while the rest are A-F (which correspond to 10-15)
						* ![[./_resources/Day_5_-_Ethernet_LAN_Switching_(Part_1).resources/image.3.png]]
				* some MAC addresses will have periods after every two digits while some have periods after every four digits
	* **Type/Length**
		* 2 byte field
		* a value of **1500 or less** in this field indicates the **LENGTH** of the encapsulated packet (in bytes)
		* a value of 1536 or greater indicates the type of the encapsulated packet (such as IPv4 or IPv6) while the length of the packet is determined by other means
		* difference between identifying an IPv4 or an IPv6 packet
			* ![[./_resources/Day_5_-_Ethernet_LAN_Switching_(Part_1).resources/image.2.png]]

**Frame Check Sequence**

* 4 bytes in length
* detects corrupted data by running a CRC algorithm over the received data
	* CRC = Cyclic Redundancy Check

The header and trailer of the Ethernet frame is 26 bytes

**QUIZ**

1. Which field of an ethernet frame provides clock synchronization?
	* preamble
2. How long is the physical address of a network device?
	* 6 bytes/48 bits

3.  What is the OUI of the following MAC address:  E8BA.7011.2874

* E8BA.70
	* the OUI (Organizationally Unique Identifier) is the first half (24 bits) of a MAC address.  It is a unique value assigned to the maker of the device.  So, it would be the first 6 digits of the 12 digit MAC address

4. which field of an ethernet frame does a switch used  to populate its MAC address table?
	* source MAC address
5. what kind of frame does a switch flood out of all of all its interfaces except the one it was received on
	* unknown unicast
		* this is a frame destined for a single host, however the switch doesn't know how to reach the destination so it  floods the frame out of all its interfaces (except the receiving one)
