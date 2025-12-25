---
---
**LAN Architectures**

* there are standard best practices for network design
* 'it depends' is an often answer to network design questions
* early stage network engineers are unlikely to be asked to design networks
	* understanding network designs is relevant to configuration/troubleshooting

**Common Terminologies - Star**

* when several devices are all connected to one central device we can draw them in a star shape
	* device diagrams may not be drawn in a star, but the point is that all the devices are connected to one central device
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.png]]

**Full Mesh design**

* when each device is connected to every other device
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.2.png]]

**Partial Mesh design**

* when some devices are connected to each other, but not all
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.1.png]]

**Two-Tier Campus LAN Design**

* the two-tier LAN design consists of two hierarchical layers
	* often called the **collapsed core** design as it omits a layer found in the Three Tier design: **Core Layer**
	* **access layer**
		* the layer that end hosts connect to (PCs, printers, cameras, etc.)
		* typically Access Layer switches have lots of ports for end hosts to connect to
		* QoS marking is typically done here
		* Security services like port security, DAI, etc. are usually performed here
		* switchports might be PoE-enabled for wireless APs, IP phones, etc.
	* **distribution layer**
		* aggregates connections from the Access Layer Switches
		* the border between Layer 2 and Layer 3
		* used to connect to services such as Internet, WAN, etc.
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.3.png]]
	* note the partial mesh design between the distribution and access layers (orange and blue)
	* there is a full mesh design among the switches on the distribution layer
* in large LAN networks with many Distribution Layer switches (such as in separate buildings), the number of connections required between Distribution Layer switches grows rapidly
	* to help scale large LAN networks, you can add a Core layer
		* Cisco recommends a core layer if there are more than three Distribution Layers in a single location
	* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.4.png]]
* **Core Layer**
	* connects distribution Layers together in large LAN networks
	* focus is on speed (fast transport)
	* CPU-intensive operations such as security, QoS marking/classification, etc. should be avoided at this layer
	* connections are all Layer 3
	* connectivity throughout the LAN should be maintained even if devices fail

**Three-Tier Campus LAN Design**

* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.5.png]]

**Spine-Leaf Architecture** 

* often  used in **data centers**
	* dedicated spaces used to store computer systems such as servers and network devices
	* traditional data center designs use a 3-tier architecture (Access-Distribution-Core) like the above
		* this all worked well when most data traffic was North-South
			* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.6.png]]
	* with the precedents of virtual servers, applications are often deployed in a distributed manner (across multiple physical servers), which increases the amount of East-West traffic in the data center
	* the traditional three-tier architecture led to bottlenecks in bandwidth as well as variability in the server-to-server latency depending on the path the traffic takes
	* to solve this, spine-leaf architecture (or Clos architecture) has become prominent in data centers
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.7.png]]
	* **rules about spine-leaf architecture**
		* every leaf switch is connected to every Spine switch
		* every spine switch is connected to every leaf switch
		* leaf switches do not connect to other leaf switches
		* spine switches do not connect to other spine switches
		* end hosts (servers, etc.) only connect to leaf switches
	* the path taken by traffic is randomly chosen to balance the traffic load among the spine switches
	* each server is separated by the same number of hops (except those connected to the same leaf), providing consistent latency for east-west traffic

**SOHO networks**

* Small Office/Home Office refers to a small company or small home office with few devices
	* a home connected to the Internet is considered a SOHO network
* SOHO networks don't have complex needs so all networking functions are usually provided by a single device (home/wireless router)
	* this one device can serve as
		* router
		* switch
		* firewall
		* wireless access point
		* modem

**QUIZ**

**![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.8.png]]**

* **b**

**![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.9.png]]**

* b
	* because the connections at the core layer are all Layer 3, STP would not be used in the core layer

![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.11.png]]

* A
	* POE (Power over Ethernet) devices such as phones, security cameras, etc. all connect to the access layer

![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.10.png]]

* b
	* endpoints like servers can connect to leaf switches and each leaf switch can connect to spine switches but **leaf switches should not connect to each other**

![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.13.png]]

* f

![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.12.png]]

* Cisco ACI = Application-Centric Infrastructure, which is comparable to spine-leaf
*  a, e
* ![[./_resources/Day_52_-_LAN_Architectures.resources/unknown_filename.14.png]]
