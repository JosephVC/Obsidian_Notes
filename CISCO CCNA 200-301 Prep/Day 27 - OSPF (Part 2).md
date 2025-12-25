---
---
**OSPF Cost**

* OSPF's metric is called **cost**
	* this is automatically calculated based on the bandwidth (speed) of the interface
	* the cost can also be manually configured
	* the **reference bandwidth** is divided by the **interface's bandwidth**
		* the default **reference bandwidth** is **100mbs**
	* **reference**: 100 mbps / **interface**:  10mbps  = **cost** of 10
	* even when the reference/interface is mathematically less than 1 , **in OSPF all values less than one are converted to 1**
		* thus FastEthernet, GigabitEthernet, etc, all have a cost of 1
	* you **should** change the reference bandwidth with the following command `auto-cost reference-bandwidth [desired mb per second]`

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.png]]

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.1.png]]

* you can also use the `bandwidth` command to change the OSPF cost of an interface by changing that interface's bandwidth
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.2.png]]
		
* there is a **difference between the interface speed and the interface bandwidth**
	* while the bandwidth and speed match by default, changing the interface bandwidth does not necessarily change the speed at which the interface operates
	* the bandwidth is just used to calculate costs and metrics
	* the `speed` command changes the speed at which the interface sends data
	* because the bandwidth value is used in OSPF metrics and costs, it's better to **not** change this value
		* use the `ip ospf cost` to change the reference bandwidth of individual interfaces

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.3.png]]

J
**OSPF Neighbors**

* the main task in troubleshooting and setting up OSPF is successfully establishing OSPF neighbors
* once routers become neighbors they automatically do the work of sharing network information, calculating routes, etc.
* when routers becomes OSPF neighbors, the router will start by sending an OSPF 'hello' message out of the interface at regular intervals (determined by the **hello timer**) which are used to introduce the router to potential OSPF neighbors
* the **default timer on a hello message** is 10 seconds on an Ethernet connection
* Hello messages are multicast to 224.0.0.5 (multicast address for all OSPF routers)
* OSPF messages are encapsulated in an IP header, with the value of 89 in the Protocol field

		**OSPF Neighbors - Down State**

* OSPF is activated on R1s G0/0
* it sends an OSPF message to 224.0.0.5
* as no other OSPF neighbors are known, the current state is **down**
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.4.png]]
	* **down** is the first OSPF neighbor state

* **OSPF Neighbor - _Init_ State**
	* when R2 receives a Hello packet, it will add an entry for R1 to its OSPF neighbor table
	* in R2's neighbor table, the relationship with R1 is now in the **init** state
		* **init state =** hello packet received , but own router ID is not in the Hello packet
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.5.png]]

* **OSPF Neighbors - 2-way state**
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.6.png]]
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.7.png]]

* OSPF Neighbors - Exstart State
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.8.png]]

* OSPF Neighbors - Exchange State
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.9.png]]

* OSPF Neighbors - Loading State
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.10.png]]

* OSPF Neighbors - Full State
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.11.png]]

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.12.png]]

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.13.png]]

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.14.png]]

**OSPF Configuration**

* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.15.png]]

* if you configure OSPF directly on the interfaces the output of `show ip protocols` will differ
	* ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.16.png]]

**QUIZ**

1. Put the OSPF Neighbor states in the correct order
	1. down state
	2. init state
	3. 2-way state
	4. exstart state
	5. exchange
	6. loading
	7. full

2. ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.17.png]]
	* c
		* these connections end up having the same cost as dividing the default reference bandwidth by the interface bandwidth comes to less than 1, the cost for these interfaces is made 1 by default

3. in which OSPF Neighbor state are the master/slave relationships decided?
	1. exstart state

4. which of the following commands can be used to give a FastEthernet interface have an OSPF cost of 100
	* `auto cost reference bandwidth 10000`

5. ![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.18.png]]
	* b) 10/40

![[./_resources/Day_27_-_OSPF_(Part_2).resources/image.19.png]]

* **the answer is 3,** as the routers will prioritized the route with the lest cost.  given the bandwidth we have, the cost of using 1Gbps is 1 (1000/1000), so our route will hop up to **RouterB, then down to RouterE, then finally to RouterC**
