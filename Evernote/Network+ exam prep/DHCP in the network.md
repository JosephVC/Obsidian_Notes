---
---
* **Static v. Dynamic IP addressing**
	* How does a computer know what it's IP configuration is
		* most often, a computer receives it's IP information from a **DHCP (Dynamic Host Configuration Protocol)** server 
		* the server not only gives a computer an IP address, but also told the PC where to find  a default **gateway** as well as how to find a DNS server
		* the compute received the IP information in one of two ways:
			* statistically (manually set) -
				* an administrator assigns an IP number and subnet mask to each host in the network
					* each network interface that will need to connect to the network will need this information
				* works fine for small, stable networks but will become unwieldy and error prone as the network grows
				* the administrator assigned a default gateway location and DNS server location to each host on the network
			* dynamically (through a service like DHCP)
* **How DHCP Works**
* **Components and Processes of DHCP**
