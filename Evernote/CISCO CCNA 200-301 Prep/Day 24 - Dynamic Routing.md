---
---
* **static routing** involves manually configuring  routes to each destination
* **dynamic routing** involves configuring a dynamic routing protocol on a router and then letting the router find the best routes to destinations
	* if a new LAN is added to the network, the dynamic routing protocol will figure out a way to get to that new destination
	* if a path to a certain destination is down, the router will find the next best way to the destination
	* this topic covers 25% of the CCNA exam
		* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.png]]

**Dynamic Routing**

* below is the network route used in this lesson

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.1.png]]

* **network route and host routes**
	* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.2.png]]
		
* dynamic routing has routers advertise their IP addresses to each other, informing the other router it can reach a destination via the router
	* each router will add this route to its routing table along with the intermediate routes in between
	* if there is an interruption between the routers, the other routers will **automatically remove** the given route from their route tables
		* we should actually make sure there is a **backup route** before completely removing a route from the routing table
		* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.3.png]]
	* in dyanamic routing, a concept similar to **root cost** is used to determine the next best route
* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.4.png]]
	
	

		

		

**Types of Dynamic Routing Protocols**

* dynamic routing protocols can be divided into two main categories
	* **Interior Gateway Protocol (IGP)**
		* used to share routes **within a single autonomous system** **(AS)** which is a single organization
			
	* **Exterior Gateway Protocol (EGP)**
		* used to share routes **between** **different autonomous systems**
	* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.5.png]]
		

**Routing Protocol Algorithm Types**

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.6.png]]

**Distance Vector Routing Protocol**

* Distance vector protocols were invented in the early 1980s, before link state protocols
* early examples are **RIPv1** and Cisco's proprietary **IGRP (and the update EIGRP)**
* distance vector protocols operate by sending directly connected neighbors the following
	* their known destination networks
	* their metric to reach their known destination networks
* this method of sharing route information is often called 'routing by rumor'
	* this is due to how a router doesn't know about the network beyond its neighbors but only knows the information that its neighbors tell it
	* this  all differs from link state protocols, where the latter try and develop a more complete picture of the network
* the **distance vector** in the name comes from how the routers only learn the 'distance' (metric) and 'vector' (direction, the next-hop router) of each route
* distance vector protocols work by sharing their routing table with neighbors

**Link State Routing Protocol**

* when using a **link state** routing protocol. every router creates a 'connectivity map' of the network
	* to allow this, each router advertises information about its interfaces (connected networks) to its neighbors; these ads are passed along to other routers until all routers in the network  develop the same map of the network
	* each router independently uses this map to calculate the best routes to a destination
* link state protocols use more CPU resources on the router as they share more information
	* despite this, link state protocols tend to be faster in reacting to changes in the network  than distance vector protocols

**Dynamic Routing Protocol Metrics**

* a router's route table contains the best route to each destination network it knows about
* if a router using a dynamic routing protocol learns two different routes to the same destination, how does it determine the best route?
	* it uses a **metric** value of the routes to determine which is best; a lower metric = better
	* each routing protocol uses a different metric to determine which route is best
* if a router learns two or more routes via **the same routing protocol** to the **same destination** with the **same metric**
	* below is the metric value of the route:
		* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.7.png]]
		* the values in the orange square are the metrics the router looks at
		* given that two routes have the same metric, the traffic will be load-balanced over both of them
			* this is **Equal Cost Multi-Path (ECMP)**
		* the values in blue are the **administrative distance (AD)**

**ECMP with Static Routes**

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.8.png]]

**Dynamic Routing Protocol Metrics**

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.9.png]]

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.10.png]]

**Administrative Distance**

* in most cases a company will only use a single IGP - usually OSPF or EIGRP
* however, in some rare cases they might use two.  for example, if two companies connect their networks to share information, two different routing protocols might be in use
* metrics are used to compare routes **learned via the same routing protocol**
* different routing protocols can't be compared as they use totally different metrics
	* OSPF route to an IP might have a metric of 30, while EIGRP to the same destination might have a metric of 33280. 
	* thus the **administrative distance (AD)** is used to determine which routing protocol is preferred
	* a lower AD is preferred, and indicates that the routing protocol is considered more 'trustworthy' (more likely to select good routes)
* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.11.png]]
	* if the administrative distance of a route is 255, the router does not believe the source of that route and does not install the route in the routing table
* ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.12.png]]

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.13.png]]

**Floating Static Routes**

* By changing the AD of a static route, you can make it less preferred than routes learned by a dynamic routing protocol to the same destination (make sure the AD is higher than the routing protocol's AD)
* the floating route will be inactive - not in the routing table - unless the route learned by the dynamic routing protocol is removed - such as when the remote router stops advertising it for some reason or an interface failure causes an adjacency with a neighbor to be lost

**QUIZ**

1. ![[./_resources/Day_24_-_Dynamic_Routing.resources/image.14.png]]

* EIGRP route only
	* when selecting among different routing protocols, the AD is the key concern for which will be added to the routing table; EIGRP has the lowest AD of the protocols

2. which type of routing protocol is also known as 'routing by rumor'
	* distance vector routing protocol

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.15.png]]

* both routes
	* both routes are to the same destination, both are via the same protocol and both have the same cost (metric = 5)

**Boson-Exim practice Q**

![[./_resources/Day_24_-_Dynamic_Routing.resources/image.16.png]]

* OSPF, as in this context you want the route with the longest prefix as this is the most specific match
	* the metric/administrative distance does not matter because the difference in prefix length means these routes are going to different destinations
	* given that the destination matches all entries for the route - only the prefix length is different, but the rest of the IP address is the same - we consider the rules of static routing
		* under these rules, we want the most **specific match, which means looking for the longest prefix match, thus OSPF**
