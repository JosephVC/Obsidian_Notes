---
---
A **computer network** is a digital telecommunications network which allows nodes to share resources.  

**What is a node?**

* **router**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.2.png]]
	* routers are needed to send data from one LAN to another
		* needed to send data over the internet
	* switches need to talk to routers in order to talk to end points on other LANs
	* have fewer network interfaces than switches 
	* one type of CISCO router is the CISCO ISR
* **switch**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.3.png]]
	* **switching means different things depending on context**
		* **ethernet switching**
			* forwarding frames based on their destination MAC address
		* **telecom switching**
			* making a connection between two parties
		* **routing**
			* the process of forwarding packets from one interface to another within a router

* used to forward traffic within a LAN, either from multiple PCs and/or from both PCs and other networked devices
* have many interfaces/ports for end hosts to connect to
* provides connectivity to hosts within the same LAN
* **by themselves, switches can't send data over the internet between other networks**
* **ethernet switch**
	* any device that forwards frames based on their L2 MAC address using Ethernet
	* only forwards frames to the ports they are destined
	* a collision domain is created on each port, whereas a hub just expands the collision domain through all ports
* **Layer 3 switch**
	* switch with routing capabilities
	* VLANS can be configured as virtual interfaces on L3 switches
	* true L3 switches are rare as most switches are multilayer switches
* **Multilayer switches**
	* like L3 switches, but can also allow for control based on higher layers in packets
	* allow for control based on TCP, UDP and also details contained in the data payload of a packet

* **firewall**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.png]]
	* special security devices that control traffic entering and exiting your network
	* can be placed outside the network or within the network
	* protects the end hosts inside
	* configured with security rules to determine which traffic should be allowed/denied
	* CISCO's classic firewall is the **ASA (Adaptive Security Appliance)**
	* modern, or **next generation firewalls** will have features such as **IPS (Intrusion Prevention System)** and other advanced filtering capabilities
	* **Network firewalls**
		* hardware devices that filter traffic between networks
	* **Host-Based Firewalls**
		* software applications that filter traffic entering and exiting a host machine (your own computer)
* **server**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.5.png]]
	* may be referred to as an **end point/end host**
	* a device that provides functions and services to clients
* **client**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.1.png]]
	* may be referred to as an **end point/end host**
	* any device can be a client, from a desktop pc to a mobile phone
		* a device that accesses a service made available by a server 
* **Internet**
	* ![[./_resources/Day_2_-_Networking_Devices.resources/unknown_filename.4.png]]

**QUIZ**

1. YOUR COMPANY WANTS TO PURCHSE SOME NETWORK HARDWARE TO WHICH THEY CAN PLUG THE 30 pcS IN YOUR DEPTARTMENT. , WHICH TYPE OF NETWORK DEVICE IS APPROPRIATE?

        - a switch

2. You receive a file from someone's phone via Airdrop.  what was the phone functioning as during the transaction

            - a server

3. As i watch a video on Youtube, what is my computer functioning as?

            - a client

4. your company wants to purchase network hardware to connect its separate networks together.  what kind of network device is appropriate?

        - a router

5. a company wants to upgrade its years-old network firewall, so what should they purchase

        - next-gen firewall
