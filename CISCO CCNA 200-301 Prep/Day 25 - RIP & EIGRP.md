---
---
**RIP - Routing Information Protocol**

* distance vector IGP (uses routing-by-rumor logic to learn/share routes)
* Uses hop count as its metric. One router = one hop (does not consider bandwidth)
* max hop count is 15, beyond which is unreachable
* Has 3 versions
	* RIPv1, RIPv2 use IPv4
	* RIPng (RIP next generation) uses IPv6
* uses two message types
	* **request:** to ask RIP-enabled neighbor routers to send their routing table
	* **response:** to send the local router's routing table to neighboring routers
* by default, RIP-enabled routers will share their routing table every 30 seconds
	* these constant updates can clog up a network

**RIPv1, RIPv2**

* RIPv1
	* do not use v1, as it is outdated
	* only advertises **classful** addresses (Class A, Class B, class C)
	* does not support VLSM, CIDR
	* doesn't include subnet mask information in ads
	* messages are broadcast to 255.255.255.255
* RIPv2
	* supports VLSM, CIDR
	* includes subnet mask information in advertisements
	* messages are **multicast** to 224.0.0.9
		* **broadcast** messages are delivered to all devices on the local network
		* **multicast** messages are delivered only to devices that have joined that **specific multicast group**

**RIP Configuration**

* simplicity of RIP is a good dynamic routing intro
* similar to OSPF configuration
* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.png]]
	* the `network` command tells the router to:
		* look for interfaces with an IP address that is in the specified range
		* activate RIP on the interfaces that fall into that range
		* form adjancencies with connected RIP neighbors
		* advertise **the network prefix on the interface** (NOT the prefix in the **network** command)
		* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.1.png]]
		* the `network` command doesn't tell the router which networks to advertise.  it tells the router which interfaces to activate RIP on, then the router will advertise the network prefix of those interfaces
		* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.2.png]]
			* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.3.png]]
				
	* the OSPF and EIGPR **network** commands operate in the same way

**EIGRP - Enhanced Interior Gateway Routing Protocol**

* was proprietary to Cisco, but Cisco published portion of the protocol, but is still considered a Cisco-only protocol
* considered 'advanced'/'hybrid' distance vector routing protocol
* much faster than RIP in reacting to changes in the network
* does not have a 15 hop count limit - supports larger networks
* sends messages using multicast address of 224.0.0.10
* is the only IGP that can perform **unequal**\-cost load-balancing (by default it performs ECMP load-balancing over 4 paths like RIP)
* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.4.png]]
		

**Wildcard Masks**

* a wildcard mask is basically an 'inverted' subnet mask
	* all 1s in the subnet mask are 0 in the equivalent wildcard mask.  All 0s in the subnet mask are 1s in the equivalent wildcard mask
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.5.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.6.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.7.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.8.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.9.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.10.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.11.png]]
	* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.12.png]]

**How to know if EIGRP is applied**

* **looking at the network mask, we determine just how many bits need to match between the original IP address and  the EIGRP network command**
* '0' in a wildcard mask = must match
* '1' in the wildcard mask = don't have to match
* ![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.13.png]]
	* converting the IP address to a wildcard mask shows us we need the first 28 bits to match between the IP and the network command
	* in the above case, they do match, so this means EIGRP will be activated on the interface

* Router ID order of priority

1. manual configuration
2. highest IP address on a loopback interface
3. highest IP address on a physical interface

**QUIZ**

![[./_resources/Day_25_-_RIP_&_EIGRP.resources/image.14.png]]

* `default-information originate`
