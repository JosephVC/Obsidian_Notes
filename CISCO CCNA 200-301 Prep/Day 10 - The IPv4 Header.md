---
---
the IPv4 header is used at L3

**OSI Model - PDUs**

* ![[./_resources/Day_10_-_The_IPv4_Header.resources/image.png]]
* the focus here will be on the L3 header, as that contains the routing data
	* at this level, the most referenced term will be **packet**

**IPv4 Header - Version field**

* Length: 4bits
* identifies the version of IP used
* IPv4 = 4(0100)
* IPv6 = (0110)
* what amounts to IPv5 was an experimental standard **internet stream protocol**, but was never publicly used

**IPv4 header - Internet Header Length (IHL)**

* length: 4 bits
* the final field of the IPv4 header (Options) is variable in length, so this field is necessary to indicate the total length of the header
* identifies the length of header in **4 byte increments**
	* if the value of the field is 5, then the total length is 5x4 bytes = 20 bytes
* the **minimum** value of the field is 5 or 20 bytes - with an empty options field
* the **maximum** value is 15 (15 x 4 bytes = 60 byte s)
* the **options field** has a max value of 40 bytes

**DSCP Field**

* Differentiated Services Code Point
* length: 6 bits
* used for QoS (Quality of Service)
* used to provide delay-sensitive data (streaming voice, video, etc.)
* used to identify which traffic ought to get priority treatment

**ECN Field**

* Explicit Congestion Notification
* Length: 2 bits
* Provides end-to-end notification of network congestion **without dropping packets**
* in a normal, busy network congestion is signaled by dropping packets
* ECN provides a way to signal congestion without dropping packets
* optional field which requires **both** end points to support it

**Total Length Field**

* Length: 16 bits
* indicates the total length of the packet (L3 header + L4 segment)
* measured in bytes (**not 4-byte increments like IHL)**
* minimum value of 20 (equal to IPv4 header with no encapsulated data)
* the max length of an IPv4 packet is 65535 bits:
	* ![[./_resources/Day_10_-_The_IPv4_Header.resources/image.1.png]]

**Identification Field**

* if a packet is fragmented from being too large, the identification field is used to identify which packet the fragment belongs to so the original packet can be reassembled
* all fragments of the same packet will have their own IPv4 header with the same value in this field
* packets are fragmented if they are larger than the maximum MTU (Maximum Transmission Unit)
	* the MTU is usually 1500 bytes
	* the MTU and the max ethernet frame are the same value
* fragments are reassembled by teh **receiving host**

**Flags Field**

* length: 3 bits
* used to control/identify fragments
* Bit 0: reserved, always set to 0
* bit 1: **Don't Fragment (DF) bit**; used to indicate a packet that should not be fragmented
* bit 2 : **More Fragments (MF)** set to 1 if there are more fragments in the packet, set to 0 for the last fragment
* if a packet is **unfragmented** the MF bit is set to 0 as there are no fragments

**Fragment Offset Field**

* length: 13 bits
* used to indicate the position of a fragment within the original, unfragmented IP packet
* allows fragmented packets to be reassembled even if the fragments arrive out of order
* the field allows the receiver to know the original order of the fragments

**Time to Live Field**

* **length: 8 bits**
* a router will drop a packet with a TTL of 0
* used to prevent infinite loops of traffic
* originally intended to indicate a packet's maximum lifetime in seconds
* in practice, indicates a 'hop count': each time a packet arrives at a router, the rounter decreases TTL by 1
* the current recommended TTL is 64

**Protocol Field**

* length: 8 bits
* indicates the protocol of the encapsulated L4PDU
* value of 6: TCP
* value of 17: UDP
* value of 1:  ICMP (the `ping` command uses this)
* value of 89: OSPF (dynamic routing protocol)

**Header checksum field**

* **length: 16 bits**
* calculated checksum to check for errors in the IPv4 packet
* when a router receives a packet, it calculates the checksum of the header and compares it to the one in this field of the header
* if they do not match, the router drops the packet
* used to check for errors only in the IPv4 header
* IP relies on the encapsulated protocol to detect errors in the encapsulated data
* both TCP and UDP have their own checksum fields to detect errors in the encapsulated data

**Source/Destination  IP Address Field**

* length: 32 bits (each)

**Options**

* **length: 0-320 bits**
* rarely used
* if the **IHL field is greater than 5**, it means that Options  are present

**Wireshark Packet Capture**

* the standard `ping`  command on a CISCO router sends 100 byte pings
	* you can use the additional `size` flag on the `ping` command to set a particular size of ping
	* you can generate an abnormally large packet which you can then see being fragmented and then reconstructed:
		* ![[./_resources/Day_10_-_The_IPv4_Header.resources/image.2.png]]
	* you can also set the ping to send a packet that is both too large and also not allowed to be fragmented, thus making the packet undeliverable:
		* ![[./_resources/Day_10_-_The_IPv4_Header.resources/image.3.png]]

**QUIZ**

1. What is the fixed binary value of the first field of an IPv4 header?

* 0100

2. Which field will cause the packet to be dropped if it has the value of 0?

* the Time to Live (TTL) field

3. How are errors in the IPv4 packet's encapsulated data detected?

* the Header Checksum field will check for errors

4. Which field of an IPv4 header is variable in length?

* options
	* can vary from 0 - 320 bits

5. which bit would be set to 1  on all IPv4 packet fragments except the last fragment?

* the More Fragments (MF) bit
