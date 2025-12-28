---
---
**Security Devices**

* **Firewall**
	* can be placed on routers or hosts (via software) or can be its own device
	* functions at 2, 3, 4, and 7 of the OSI model
	* blocks packets from entering or leaving the network
		* **via stateless inspection**
			* the firewall will examine every packet against a set of rules; as the packet matches the rules, and the rules are enforced, the specified action is taken
		* **via statefull inspection**
			* the firewall will only examine the the state of the connection between networks
			* when a connection is made between internal/external networks, the firewall will not examine any packets returning from the **external** network 
			* as a general rule external connections are not allowed to be made from the internal network
	* the first line of defense to protect the internal network against threats
* **Intrusion Detection System (IDS)**
	* the IDS is a passive system for detecting when a network intrusion has occured
		* meant to inform the network admin via text, email, etc.
	* cannot stop an attack/breach on its own
	* receives a copy of all traffic and compares it to a set of standards
		* **signature based**
			* evaluates network traffic for known malware or attack signatures
		* **anomaly based**
			* evaluates network traffic for suspicious changes
		* **policy based**
			* evaluates traffic against a specific desired policy
	* may be deployed at the host level
		* **HIDS (Host-based Intrusion Detection System)**
* **Intrusion Prevention System (IPS)**
	* an active system meant to stop an attack 
		* usually performs an action or set of actions to stop an attack
		* will inform a network admin through the use of log files, SMS, or email notification
	* all traffic on a particular segment of the network flows through the IPS to either enter or leave the segment
		*  all traffic is compared to a set of standards
	* the best place to put it is between the router (with a firewall) and the destination network segment
	* programmed to make an active response to a situation
		* block an offending IP address
		* close down a vulnerable interface
		* terminate the network session
		* redirect the attack
* **Virtual Private Network (VPN) Concentrator**
	* provides proper tunnelling and encryption
	* function at multiple layers of the OSI model (2, 3, 7)
		* outside of internet transactions (using SSL VPN connection at layer 7) will work at layer 3, providing **IPSec** encryption through a secure tunnel

**Optimization and Performance Devices**

* **Load Balancer**
	* can also be called a **content switch** or **content filter**
	* a network appliance is used to load balance across multiple hosts that contain the same data
	* spreads out workload for greater efficiency 
* **Proxy Server**
	* **![[./_resources/Introduction_to_Network_Devices_II.resources/unknown_filename.png]]**
	* requests resources on behalf of client machines
	* often used to retrieve resources from outside (untrusted) networks on behalf of the requesting client
	* hides and protects the requesting client
	* can be made to filter allowed content
	* can increase network performance by caching commonly requested web pages
