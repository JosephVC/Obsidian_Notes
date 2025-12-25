---
---
**Configuring IPv6 addresses (EUI-64)**

* **EUI** stands for Extended Unique Identifier
* (**Modified) EUI-64** is a method of converting  a MAC address (48 bits) into a 64-bit interface identifier
	* allows routers to automatically create a IPv6 address by expanding their MAC address to a 64 bit ID which is then combined with the specified IPv6 prefix
* This interface identifier can then become the 'host portion' of a /64 IPv6 address
* How to convert the MAC address:
	* this is likely to be done automatically on a router, but know it anyway
	* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.png]]

* **step 3 involves both looking up the hex value of the 2nd number, but then inverting the 3rd bit of that value - the 7th bit**
	![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.13.png]]
	

* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.1.png]]

**Why invert the 7th bit?**

* MAC address can be divided into two types
	* UAA (Universally Administered Address)
		* Uniquely assigned to the device by the manufacturer
	* LAA (Locally Administered Address)
		* Manually assigned by an admin (with the **mac-address** command on the interface) or protocol; **does not have to be globally unique**
* you can identify a UAA or LAA by the 7th bit of the MAC address, called the **U/L bit (Universal/Local bit)**
	* **U/L** bit set to 0 = UAA
	* U/L bit set to 1 = LAA
* In the context of IPv6 addresses/EUI-64, the meaning of the U/L  bit is reversed
	* U/L bit set to 0 = the MAC address the EUI-64 interface ID was made from was an LAA
	* U/L bit set to 1 = the MAC address the EUI-64 interface ID was made from was a UAA

**Global Unicast Address**

* global unicast IPv6 addresses are public addresses which can be used over the Internet
* you must register to use them; because they are public addresses it is expected that they are globally unique
* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.2.png]]

**Unique Local Addresses**

* Unique local addresses are addresses that **cannot** be used over the internet
* no need to register them; can be used freely within **internal** networks and don't need to be globally unique (although you should try and make the addresses unique)
	* while you can try using these addresses over the internet, your ISP will likely drop packets
* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.3.png]]

**Link Local Addresses**

* **link-local** addresses are automatically created when you set up an IPv6 address
* use the command ipv6 enable on an interface to enable IPv6 on an interface
	* this will generate a link local address and this will be the only IPv6 address on the interface
* Link local means these addresses will be used for communicating within a single link (subnet)
	* routers **will not** route packets with a link-local destination IPv6 destination IPv6 address
* common usage of local-link addresses:
	* routing protocol peerings (OSPFv3 uses link-local addresses for neighbor adjacencies)
	* next hop addresses on static routes
	* **Neighbor Discovery Protocol (NDP,** IPv6's replacement for ARP) uses link-local addresses to function
* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.4.png]]

* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.5.png]]

**Multicast Addresses in IPv6**

* **unicast** addresses are one-to-one
	* one source to one destination
* **broadcast** addresses are one-to-all
	* one source  to all destinations (within the subnet)
	* **IPv6 does not use broadcast, as there is no broadcast address**
* **multicast** are one-to-many
* one source to multiple destinations (that have joined the specific **multicast group)**
	* **the below info in the orange square is a multicast group**
		* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.7.png]]
			
* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.6.png]]

**Multicast Address Scopes**

* IPv6 defines multiple multicast address 'scopes' which define how far each packet should be forwarded
* IPv6 multicast scopes
	* **Interface Local (FF01)** - the packet doesn't leave the local device; can be used to send traffic to a service within the local device
	* **Link-Local (FF02)** - the packet remains in the local subnet; routers will not route the packet between subnets
	* **Site local (FF05) -** can be forwarded by routers; should be limited to a single physical location (not forwarded over a WAN)
	* **Organization local (FF08)** - wider is scope than site local, such as a whole company/organization
	* **global (FF0E)** - no boundaries; possible to be routed over the internet
		

**Anycast Address**

* new feature of IPv6
* one-to-one-of-many
	* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.8.png]]
* multiple routers are configured with the same IPv6 address
	* they use a routing protocol to advertise the address
	* when hosts send packets to that destination address, routers will forward it to the nearest router configured with that IP address (based on routing metric)
* there is no specified range for anycast addresses ; use a regular unicast address (global unicast, unique local) and specify it as an anycast address
	* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.9.png]]

**Anycast address configuration**

* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.10.png]]
	* we know this interface is set up for anycast even though it is claims to be a Global unicast address because of the bracketed ANY

**Other IPv6 addresses**

* ![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.11.png]]

**QUIZ**

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.12.png]]

* d)

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.14.png]]

* B)

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.15.png]]

* D
	* as this goes to all routers

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.16.png]]

* C)

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.17.png]]

![[./_resources/Day_32_-_IPv6_(Day_2).resources/image.18.png]]

* **not routable** means that if the router receives a packet, the packet will not route the packet
* B), F)
	* these are link local addresses, which IPv6 does not route
