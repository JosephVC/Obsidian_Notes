---
---
**Network Automation**

* previous versions of the CCNA have focused on the traditional model of managing/controlling networks
* the current version focuses on the traditional model as well, , but basics of network automation are expected to be understood
* traditionally, engineers managed devices one at a time by connecting to their CLI via SSH
* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.png]]
	* **downsides of managing devices by hand**
		* typos
		* time-consuming and inefficient at scale
		* difficulty in ensuring that all devices adhere to the org's standard configurations
	* **key benefits of automation**
		* typos and other human errors are reduced
		* networks become more scalable;  new deployments, network-wide changes, and troubleshooting can be implemented faster
		* network-wide policy compliance can be assured (standard configurations, software versions, etc.)
		* the improved efficiency  of network operations reduces the opex (operating expenses) of the network; fewer man hours are needed
		* **Àvarious networking automation tools**
			* SDN (Software Defined Networking)
			* Ansible
			* Puppet
			* Python scripting

**Logical 'planes'**

* **What does a router do?**
	* it forwards messages between networks by examining information in the Layer 3 header
	* it uses a routing protocol like OSPF to share route information with other routes and build a routing table
	* it uses ARP to build and ARP table, mapping IP addresses to MAC addresses
	* also uses **syslog** to keep track of events
	* allows users to connect to SSH and manage it
* **What does a switch do?**
	* forwards messages within a LAN by examining information in the L2 header
	* uses STP to ensure there is no L2 loops in the network
	* it builds a MAC address table by examining the source MAC address of frames
	* it uses Syslog to keep logs of events that occur
	* allows users to connect via SSH and manage it

**The various functions of network devices can be logically divided up into _planes_**

* **data plane**
	* all tasks involving forwarding user data/traffic from one interface to another are part of the data plane
	* a router receives a message, looks for the most specific matching route in its routing table, and forwards it out the appropriate interface to the next hop
		* it also de-encapsulates the original L2 header, and re-encapsulates it with a new header destined for the next hop's MAC address
	* a switch receives a message, looks at the destination MAC address, and forwards it out the appropriate interface (or floods it)
		* this includes functions like adding or removing 802.1q (dot1q) VLAN tags
	* NAT (changing the src/dst addresses before forwarding) is part of the data plane
	* deciding to forward or discard messages due to ACLs, port security, etc. is part of the data plane
	* another name for the data plane is the **forwarding plane**, as  forwarding messages is what the data plane does
	* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.1.png]]
		
* **control plane**
	* how does a device's data plane make its forwarding decisions?
		* routing table, MAC address table, ARP table, STP, etc.
	* functions that build these tables (and other functions that influence the data plane) are part of the **control plane**
		* the control plane **controls** what the data does, for example, by building the router's routing table
	* the control plane performs **overhead work**
		* OSPF itself doesn't forward user data packets, but it informs the data plane about how packets should be forwarded
		* STP itself isn't directly involved in the business of forwarding frames, but it informs the data plane about which  interfaces should and shouldn't be used to forward frames
		* ARP messages aren't user data, but they are used to build an ARP table which is used in the process of forwarding data
		* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.2.png]]
		* the operations of the Management and Control plane are usually managed by the CPU
		* this is not desirable for data plane operations because CPU processing is relatively slow
			* rather, a specialized hardware **ASIC (Application-Specific Integrated Circuit)** is used.  ASICS are chips built for specific purposes.
		* using a switch as an example
			* when a frame is received, the ASIC - not the CPU - is responsible for the switching logic
			* the MAC address table is stored in a kind of memory called **TCAM (Ternary Content-Addressable Memory)**
				* another common name for the MAC address table is **CAM table**
				* TCAM returns the matching MAC address table entry
					* the frame is then forwarded out of the appropriate interface
		* modern routers also use a similar hardware data plane: an ASIC designed for forwarding logic, and tables stored in TCAM
		* **when a device receives control/management traffic (destined for itself), it will be processed by the CPU**
		* **when a device receives data traffic which should pass through the device, it is processed by the ASIC for maximum speed**
* **management plane**
	* also performs overhead work like the control plane
		* the difference is that the mgmt plane does not directly control the forwarding of messages in the data plane
	* the management plane consists of protocols that are used to manage devices
		* SSH/Telnet, used to connect to the CLI of a device to configure/manage it
		* Syslog, used to keep logs of events that occur on the device
		* SNMP, used to monitor the operations of a device
		* NTP, used to maintain accurate time on the device
		* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.3.png]]
			* the **data plane** is the reason we buy routers and switches, in addition to other network infrastructure tools, **to forward messages**.  However, the control plane and management plane are both necessarily to enable the data plane to do its job

**Software Defined Networking - SDN**

* an approach to networking that centralizes the control plane into an application called a **controller**
	* this is a similar concept from **WLC (Wireless LAN Controllers)**
		* using a WLC, many functions are removed from the AP to the controller, so the AP is more free to forward traffic
* SDN is also called **Software-Defined Architecture (SDA)** or **Controller-Based Networking (CBN)**
* traditional control planes use a distributed architecture
	* as an example, each router in the network runs OSPF and the routers share routing information and then calculate their preferred routes to each destination
* an SDN controller centralizes control plane functions like calculating routes
	* how much the control plane is centralized varies greatly
* the controller can interact programmatically with the network devices using APIs
* a **Southbound Interface (SBI)** is a software interface the handles the communication between the controller itself and the other communication devices
	* called **southbound** as the controller is generally drawn on top of the SBI when making diagrams, with the other network devices drawn below the SBI
* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.4.png]]

**Southbound Interface (SBI)**

* used for communication between the controller and the network devices it controls
* typically consists of a communication protocol and API 
	* while not SBIs themselves, APIs facilitate data exchange between programs
		* data is exchanged between the controller and the network devices
		* and API on the network devices allows the controller to access information on the devices, control their data plane tables, etc.
* some examples of SBIs
	* OpenFlow
	* Cisco OpFlex
	* Cisco onePK (Open Network Environment Platform Kit)
	* NETCONF

**Northbound Interface (NBI)**

* using the SBI, the controller communicates with managed devices and gathers information on them
	* the devices in the network
	* the topology (how devices are connected together)
	* the available interfaces on each device
	* their configurations
* the **Northbound Interface (NBI)** is what allows us to interact with the controller, access the data it gathers about the network, and make changes in the network via the SBI
* a **REST API** is used on the controller as an interface for apps to interact with it
* ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.5.png]]

**Automation in Traditional Networks v SDN**

* networking tasks can be automated in traditional network architectures too
	* scripts can be written using Python to push commands to multiple devices at once
	* Python with good use of **regular expressions** can parse through **show** commands to get information about the network devices
* the robust and centralized data collected by SDN controllers greatly facilitate these functions
	* the controllers collects information about all devices in the network
	* northbound APIs allow apps to access information in a format that is easy for programs to understand (JSON, XML)
	* the centralized data facilitates network-wide analytics
* SDN tools can provide the benefit of automation without the requirement of third-party scripts and apps
	* you don't need expertise in automation to make use of SDN tools
	* APIs allow third-party applications to interact with the controller, which has powerful uses
* Although SDN and automation aren't the same thing, the SDN architecture greatly facilitates the automation of various tasks in the network via the SDN and APIs

**QUIZ**

1. ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.6.png]]
	* a, b
		* OpEx just means operating expenses, which go down when you are able to enter commands faster and more efficiently via automation

2. ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.7.png]]
	* c, d

3. ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.8.png]]
	* a
		* all the rest of the functions belong to the data plane, as they regarding forwarding messages
		* calculating routes is a control plane function, thus would likely be centralized in a CDN

4. ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.9.png]]
	* c

5. ![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.10.png]]
	* b
		* NTP is used to provide accurate time, and does not forward messages or control how the data plane operates, so operates at the mgmt plane

![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.11.png]]![[./_resources/Day_59_-_Intro._to_Network_Automation.resources/image.12.png]]
