---
---
**SDN Review**

* **SDN (Software Defined Networking)** is an approach to networking that centralizes the control plane into an application called a **controller**
* traditional control planes use a distributed architecture
* an SDN controller centralizes control plane functions like calculating routes
* the controller can interact programmatically with the network devices using APIs
* the **SBI (Southbound Interface)** is used for communications between the controller and the network devices it controls
* the **NBI (Northbound Interface)** is used to interact with the controller with our scripts and applications

**SDN Architecture**

* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.png]]

**SD-Access**

* Cisco **SD-Access** is Cisco's SDN solution for automating campus LANs
	* **ACI (Application Centric Infrastructure)** is their SDN solution for automating data center networks
	* **SD-WAN** is their SDN solution for automating WANs
* Cisco **DNA (Digital Network Architecture) Center** is the controller at the center of SD-Access
	* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.1.png]]
		* **The Fabric layer**
			* the **underlay** is the underlying physical network of devices and connections (including wired and wireless) which provide IP connectivity (ie using IS-IS)
				* multilayer switches and their connections
					
				* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.2.png]]
				* the underlay's purpose is to support the VXLAN tunnels of the overlay
				* there are three different roles for switches in SD-Access
					* **edge nodes:** connect to end hosts
					* **border nodes:** connect to devices outside of the SD-Access domain, ie WAN routers
					* **control nodes:** uses **LISP (Locator ID Separation Protocol)** to perform various control plane functions
				* you can add SD-Access on top of an existing network (**brownfield deployment)** if your network hardware and software supports it
					* search 'cisco sd-access compatibility matrix' if  curious which devices support this
				* a new deployment (**greenfield deployment)** will be configured by DNA Center to use the optimal SD-Access underlay
					* all switches are L3 and use IS-IS as their routing protocol
					* all links between switches are routed ports.  this means STP is not needed
					* edge nodes (access switches) act as default gateway of end hosts (**routed access layer)**
					* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.5.png]]
						
			* the **overlay** is the virtual network built on top of the physical underlay network
				* SD-Access uses **VXLAN (Virtual Extensible LAN)** to build tunnels
				* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.3.png]]
				* LISP provides the control plane of SD-Access
					* a list of mappings of **EIDs (Endpoint Identifiers)** to **RLOCs (Routing Locators)** is kept
					* EIDs identify end hosts connected to edge switches, and RLOCs identify the edge switch which can be used to reach the end host
				* **Cisco TrustSec (CTS)** provides policy control (QoS, security policy, etc.)
				* VXLAN provides the data plane of SD-Access
					* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.6.png]]
						
			* the **fabric** is the combination of the overlay and underlay; the physical and virtual network as a whole
				* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.4.png]]

**Cisco DNA Center**

* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/image.7.png]]
	
* has two main roles
	* the SDN controller in SD-Access
	* a network manager in a traditional network (non-SD-Access)
* DNA Center is an application installed on Cisco UCS server hardware
* it has a REST API which can be used to interact with the DNA center
* the SBI supports protocols such as NETCONF and RESTCONF (as well as traditional protocols like Telnet, SSH, SNMP)
* DNA Center enables **Intent-Based Networking (IBN)**
	* the goal is to allow the engineer to communicate their intent for network behavior to the DNA Center, and then the DNA Center will take care of the details of the actual configurations and policies on devices
	* traditional security policies using ACLs can become VERY  cumbersome
		* ACLs have thousands of entries
		* the intent of entries is forgotten with time and as engineers leave and new engineers take over
		* configuring and applying ACLs correctly across a network is cumbersome and leaves
* DNA Center allows the engineer to specify the intent of the policy - this group of users can't communicate with this group, this group can access this server  but not that server - and DNA Center will take care of the exact details of implementing policy
* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.png]]

**DNA Center vs Traditional Network Management**

* **Traditional network management**
	* devices are configured one-by-one via SSH or console connection
	* devices are manually configured via console connection before being deployed
	* configurations and policies are managed per-device
	* new network deployments can take a long time due to the manual labor requied
	* errors and failures are more likely due to increased manual effort
* **DNA Center-based network management**
	* devices are centrally managed and monitored from the DNA Center GUI or other applications using its REST API
	* the administrator communicates their intended network behavior to DNA Center, which changes those intentions into configurations on the managed network devices
	* configurations and policies are centrally managed
	* software versions are also centrally managed.  DNA Center can monitor cloud servers for new versions and then update the managed devices
	* new network deployments are much quicker.  New devices can automatically recieve their configurations from DNA Center without manual configuration

**QUIZ**

1. ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.2.png]]
	* A

2.  
	![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.1.png]]
	* B

3. ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.4.png]]
	* B

4. ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.3.png]]
	* D
	* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.7.png]]

5. ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.6.png]]

* A, C , D

6. ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.8.png]]

* ![[./_resources/Day_62_-_SDN_(Software_Defined_Networking).resources/unknown_filename.5.png]]
