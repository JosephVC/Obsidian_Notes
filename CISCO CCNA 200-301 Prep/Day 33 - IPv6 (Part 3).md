---
---
**IPv6 Address Representation**

* so, an RFC (Request For Comment) is a publication from the ISOC (Internet Society) and associated orgs like the IETF (Internet Engineering Task Force) and are the official docs of Internet specs. protocols, etc.
* RFC 5952: **A Recommendation for IPv6 Address Text Representation**
	* before this, IPv6 text representation was flexible
	* this suggests standardizing IPv6 representation
		* **leading 0s must be removed**
		* **double colons must be used to shorten the longest string of all-0 quartets**
		* **if there are two equal-length choices for double colons, shorten the group on the left**
		* **Hexadecimal characters a-f \*must\* be written in lowercase rather than uppercase**

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.png]]

* in contrast to IPv4, IPv6 has a **fixed** header length of 40 bytes

**IPv6 Header - Version**

* length = 4 bits
* indicates the version of IP that is used
* fixed value of 6 (0b010) to indicate IPv6

**IPv6 Header - Traffic Class**

* length = 8 bits
* used by QoS (Quality of Service) to indicate high priority traffic
	* IP phone traffic, live video calls have a high priority over other traffic

**Flow Label**

* length = 20 bits
* used to identify specific traffic flows - a communication between a specific source and destination

**Payload Length**

* length = 16 bits
* indicates the length of the payload (encapsulated L4 segment) **in bytes**
* the length of this header is not included, as it is fixed at 40 bytes

**next header**

* length = 8 bits
* indicates the type of 'next header' ( header of the encapsulated segment), such as TCP or UDP
* functions the same as IPv4's **protocol** field

**Hop Limit**

* length = 8 bits
* the value is decremented by 1 each time a router forwards it, and the packet is discarded when this number reaches 0
	* functions the same as an IPv4 TTL field

**Source/Destination**

* length = 128 bits each
* fields contain the IPv6 addresses of the packet's source and destination

**Solicited Node Multicast Address**

* an IPv6 solicited-node multicast address is calculated from a unicast address
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.1.png]]

* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.2.png]]
	* the address in the above yellow rectangle is the solicited node multicast address

**Neighbor Discovery Protocol (NDP)**

* protocol used with IPv6
* as essential to IPV6 routing as ARP is to IPv4 routing
* it functions like ARP to use ICMPv6 and solicited-node multicast addresses to learn the MAC addresses of other hosts
	* ARP uses broadcast messages
	* solicited node multicast messages are aimed at a specific  host, thus are more efficient than ARP
* two message types are used
	1. neighbor solicitation (NS) message = ICMPv6 type 135
	2. neighbor advertisement (NA) message = ICMPv6 type 136

**Neighbor Solicitation (NS)**

* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.3.png]]

**Neighbor Advertisement (NA)**

* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.4.png]]

**IPv6 Neighbor Table**

* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.5.png]]

**Neighbor Discovery Protocol**

* Another function of NDP allows hosts to automatically discover router on the local network
* two messages are used for this process
	1. Router solicitation (RS) = ICMPv6 Type 133
		* Sent to multicast address FFO2::2 (all routers)
		* Asks all routers on the local link to identify themselves
		* Sent when an interface is enabled/host is connected to the network

2.    Router advertisement (RA) = ICMPv6 Type 134

* Sent to multicast address FF02::1 (all nodes)
* the router announces its presence, as well as other information bout the link
* these messages are sent in response to RS messages

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.6.png]]

**SLAAC (Stateless Address Auto-Configuration)**

* hosts the RS/RA messages to learn the IPv6 prefix of the local link and then automatically generate an IPv6 address
* using the `ipv6 address [prefix/prefix-lenth eui-64` command, you need to manually enter the prefix
* using the `ipv6 address autoconfig` command, you don't need to enter the prefix . The device uses NDP to learn the prefix used on the local link
* The device will use EUI-64 to generate the interface ID, or it will be randomly generated (depending on the device/maker)
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.7.png]]
	

**Duplicate Address Detection (DAD)**

* allows hosts to check if other devices on the local link are using the same IPv6 address
* any time IPv6-enabled interface initializes (`no shutdown` command) or an IPv6 address is configured on an interface (by any method, manual, SLAAC, etc.) it performs DAD
* DAD uses two messages you learned earlier: NS and NA
* the host will send an NS to its own IPv6 address; if it doesn't get a reply it knows the address is unique
* if it gets a reply, it means another host on the network is already using the address

**IPv6 Static Routing**

* IPv6 routing works the same as IPv4 routing
	* the two processes are separate on the router, and the two routing tables are separate
* on Cisco routers, IPv4 is enabled by default
	* IPv6 routing needs to be enabled by `ipv6 unicast-routing` command
* if IPv6 routing is disabled, the router will be able to send and receive IPv6 traffic, but will not be able to route - forward between networks - IPv6 traffic
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.8.png]]
	
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.9.png]]
	* the **command specified in curly braces are mandatory while those in square brackets are optional**, meaning here you need to specify the next hop or an exit interface (with an optional next hop)
	* given the constraint in the yellow , you will still be able to use the static route command, but it won't actually work
	* **on IPv6 address will need to be configured with either a recursive static route or a fully specified static route**
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.10.png]]
	* the `::/0` portion of the command is equivalent to `0.0.0.0.0` in IPv4
	* all the routes above are recursive, as they don't specify the exit interface on the router
* **Floating static route**
	* by raising the `ad` argument when setting up IPv6 routes, we can make static backup routes - floating static routes
		* if the main route to a destination was learned through OSPF (for example), you would need to set the static route's administrative distance to higher than 110, because OSPF's admin. distance is 110
			* **always set the administrative distance higher than the main route**

**Link-local next hop**

* a **fully specified static route** is when both the next hop and exit interface are specified
* these attributes need to be fully specified as with a link-local next hop address, the router alone can't figure out which interface the next hop is connected to
* ![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.11.png]]

**QUIZ**

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.12.png]]

* NA

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.13.png]]

* D)
	* when an IPv6 address is configured on an interface, the router will send an NS message to the interface's own solicited multicast address

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.14.png]]

* because it is router advertisement, it uses the FF02::1 multicast address

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.15.png]]

* A, B
	* fully specified as it specifies an exit interface and next hop
	* network because it's destination is a network rather than another host

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.16.png]]

* c

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.17.png]]

![[./_resources/Day_33_-_IPv6_(Part_3).resources/image.18.png]]
