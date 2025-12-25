---
---
OSPF is topic 3.5 on the CCNA
![[./_resources/Day_26_-_OSPF_Part_1.resources/image.png]]

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.1.png]]

**Link State Routing Protocol**

* when using a **link state** routing protocol, every router creates a 'connectivity map' of the network
	* to allow this, each router advertises its interface information (connected networks) to its neighbors.  These advertisements are passed along to other routers, until all routers in the network develop the same map of the network
* each router independently uses this map to calculate the best routes to each destination
* link state protocols use more resources (CPU) on the router, because more information is shared
* link state protocols tend to be faster in reacting to changes in the network than distance vector protocols

**OSPF - Open Shortest Path First**

* uses **shortest path first** algo. created by Edsger Dijkstra (**Dijkstra's algorithm)**
* three version of OSPF
	* v1 (1989) - not in use anymore
	* v2 (1998) - used for IPv4
	* v3 (2008) - used for IPv6 (can also be used for IPv4, but usually v2 is used for this)
* routers store information about the network  in **Links State Advertisements (LSAs)** which are organized in a structure called the **Link State Database (LSDB)**
* routers will **flood** LSAs until all routers in the OSPF **area** develop the same map of the network **(the LSDB)**
* In OSPF, there a **three main steps** in the process of sharing LSAs and determining the best route to each destination in the network
	1. **become neighbors** with other routers connected to the same segment
	2. **exchange LSAs** with neighbor routers
	3. **calculate the best routes** to each destination, and insert them into the routing table

**LSA Flooding**

* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.2.png]]
	* each LSA has an aging timer (30 min. by default); the LSA will be flooded again after the timer expires

**OSPF Areas**

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.3.png]]

* OSPF uses **areas** to divide up the network
* an **area** is a set of routers and links that share the same LSDB
* small networks can be **single-area** without any negative effects on performance
* in larger networks a single-area  design can have negative effects
	* the SPF algorithm takes more time to calculate routes
	* the SPF algo. takes exponentially more time on the routers
	* the larger LSDB takes up more memory on the routers
	* any small change in the network causes every router to flood LSAs and run the SPF algo. again
* by dividing a large OSPF network into several smaller areas, you an avoid the above negative effects
* **Area 0** is called the **backbone** area
	* the backbone area is an area that **all other areas must connect to**
		* if any one of the above areas tried to connect to one another rather than to the backbone, it would not be allowed
* routers with all interfaces in the same area are called **internal routers**
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.4.png]]
* routers with interfaces in multiple areas are called **area border routers (ABRs)**
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.5.png]]
	* ABRs maintain a separate LSDB for each area they are connected to .  it is recommended that you connect an ABR to a max. of 2 areas.  Connecting and ABR to 3+ areas can overburden the router
* routers connected to the backbone area (area 0) are called **backbone routers**
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.6.png]]
* an **intra-area route** is a route to a destination inside the same OSPF area
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.8.png]]
	* an **internal router** has all its interfaces in the same area

* an **interarea route** is a route to a destination  in a different OSPF area
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.7.png]]

* OSPF areas should be **contiguous**
	* each individual area should be connected
	* you **can't** divide networks up, but rather have a series of single networks - areas - basically next to each other
* all OSPF areas must have at least one ABR connected to the backbone area
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.9.png]]
		* the above is correct, but the below is not correct as it is not connected to a backbone:
			* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.10.png]]
* OSPF interfaces in the same subnet must be in the same area

**Basic OSPF Configuration**

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.11.png]]

* the **network** command tells OSPF to
	* look for any interfaces with an IP address contained in the range specified in the **network** command
	* activate OSPF on the specified area
	* the router will then try to  become OSPF neighbors  with other OSPF-activated routers

**`passive interface` command**

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.12.png]]

**Advertise a Default Route into OSPF**

* add the ISPs default route
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.13.png]]
* \`default-information originate\`  is the command to advertise the default route

`show ip protocols`

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.14.png]]

* the command `reset ALL OSPF processes` is a bad idea in the field, as resetting OSPF on the router causes the router to lose all OSPF routes and thus temporarily lose the ability to forward those routes
	* the option in brackets is the default option

* an **autonomous system boundary router** (ASBR) is an OSPF that connects the OSPF network to an external network
	* ![[./_resources/Day_26_-_OSPF_Part_1.resources/image.22.png]]
		
* R1 is connected to the internet; by using the **default-information originate** command, R1 becomes an ASBR

**QUIZ**

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.15.png]]

* b, f
	* in a single-area OSPF, you can use any area
	* in multiple area OSPF, there will be multiple areas operating in a single process, thus it's impossible to match the process ID to all areas IDs

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.16.png]]

* c
	* this is the only option that contains both IP addresses in its range, so it's the only one that activates OSPF on its interfaces

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.17.png]]

1. there are four backbone routers
2. there are three ABRs
3. there is one ASBR

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.18.png]]

* b
	* first a default route is configured and then advertises it into OSPF using the `default-information originate` command

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.19.png]]

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.20.png]]

![[./_resources/Day_26_-_OSPF_Part_1.resources/image.21.png]]
