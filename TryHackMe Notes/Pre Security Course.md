---
---
**What is Networking?**

Devices on a network need a name and personal fingerprint in order to properly operate.  The **name** of a device is the **IP address,** while the **fingerprint** is the **MAC** address.

**IP Addresses**

an IP address is divided up  into **four octets:**
![[./_resources/Pre_Security_Course.resources/image.png]]
the value of an octet is determined by **IP addressing and subnetting**, a more advanced topic

a device can have a **public** and **private** IP address.   the public IP is used to identify devices on the internet, while the private IP is used to identify devices among each other

![[./_resources/Pre_Security_Course.resources/image.1.png]]
the **public** IP address will be established by one's ISP

given the quantity of devices in the world, there needs to be a way to ensure there are enough IP addresses go around.  **IPv4** is still in use, and gives us the above numbering scheme of four octets.  **IPv6** is a new standard that allows up to 2^128 IP addresses, and can be more efficient:

![[./_resources/Pre_Security_Course.resources/image.2.png]]

**MAC addresses**

the physical electronic component that resides in every network-capable device has a MAC address applied to it at the factory.  the address is a 16 character hexadecimal number where the first six numbers represent the manufacturer and the last six are unique to the device:

* ![[./_resources/Pre_Security_Course.resources/image.3.png]]
* a MAC address can be **spoofed** whereby a devices pretends to have a different MAC address

**Ping**

the ping command is fundamental in networking

Ping uses **ICMP (Internet Control Message Protocol)** packets to determine the performance of the connection between devices, such as whether the performance is reliable or not, or how long it takes to reach connections (using ICMP's **echo packet** and **echo response)**

**Intro to LAN**

* **Ring topology**
	* packets travel around a network in a ring formation, in a single direction, so if there is an interruption in any portion of the ring the packets can no longer travel
		
* **Bus Topology**
	* all devices are connected to a single cable, often referred to as the **backbone**
	* data is sent in all directions until the packet's destination is reached
	* a flaw is that the bus topology can't handle large amounts of data
		* the bus network can crash if too much traffic tries to be sent at once
		* cost effective
* **Star topology**
	* all devices are connected via their own cable to a central switch/hub
	* if the switch goes down, the network does too
	* this is the most common topology based on reliability and scalability, despite costing more
* **Router**
	* the router connects networks to other networks
	* routing is useful for when devices are connected via many paths
* **Switches**
	* devices within a network meant to aggregate multiple devices (computers, printers, etc.) within the same network
	* switches do not perform routing
	* use **packet switching** to break down packets into smaller, more manageable pieces
		* large packets can slow down a  network

**Primer on Subnetting**

* **subnetting** allows network admins to categorize and assign specific parts of the network to reflect the need to send information to the correct department
* you subnet when you split up the number of hosts that can fit into a network
	* this number is the **subnet mask**
		* the subnet mask is made up of 8 bytes (32 bits) ranging from 0-225

* subnets use IP addresses in 3 different ways
	* identify the network address
	* identify the host address
	* identify the default gateway
* ![[./_resources/Pre_Security_Course.resources/image.4.png]]
	
* on a small network like a home there will likely be one subnet, while in a business there will be a greater need for subnets
* the value of subnetting is **efficiency, security, full control**
* for example, a coffee shop will subnet in a way to give one network to staff and another network for customers

**The ARP Protocol**

* using the two identifiers we  have for a device on a network, the **ARP protocol (Access Resolution Protocol)** is responsible for allowing devices to identify themselves on a network
* ARP allows a device to associate its MAC address with an IP address on the network
* each device will keep a log of the MAC addresses associated with other devices
* when devices wish to communicate with each other, they will broadcast to the entire network searching for a specific device; the ARP protocol can be used to find the MAC address of a device

* **How does ARP work?**
	* each device on a network stores the identifiers of other networked devices on a **cache**
	* in order to map the IP and MAC address of a device together, ARP sends two messages
		* ARP request
			* a message is broadcast to every other device on the network, asking whether a given device's MAC address matches the requested IP address
				
		* ARP Reply
			* this reply is sent if a device has the IP address requested in ARP request, acknowledging the fact
			* the initial device remembers and stores the answer in its cache (**ARP entry)**
	* ![[./_resources/Pre_Security_Course.resources/image.5.png]]

**DHCP Protocol**

* You can either manually specify a device's IP address, or you can use **DHCP** (Dynamic Host Configuration Protocol) to do so automatically
* if a networked device does not already have an IP address it sends out a request (**DHCP discover)** to see if there any any DHCP servers on the network
* the DHCP server then replies with the **DHCP offer** of an IP address the given device can use
* the device sends a **DHCP request** confirming it wants the offered IP address
* the DHCP server finally sends back an acknowledgement that the address can now be used - the **DHCP ACK**
* ![[./_resources/Pre_Security_Course.resources/image.6.png]]
