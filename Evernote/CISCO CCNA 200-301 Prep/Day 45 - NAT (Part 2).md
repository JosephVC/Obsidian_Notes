---
---
**Static NAT**

* involves statically configuring one-to-one mappings of private IP addresses to public IP addresses
* when traffic from the internal host is sent to the outside network, the router will translate the source address
* one-to-one mapping also allows external hosts to access the internal host via the inside global address
* ![[./_resources/Day_45_-_NAT_(Part_2).resources/unknown_filename.png]]

**Dynamic NAT**

* in dynamic NAT, the router dynamically maps **inside local** addresses to **inside global** addresses as needed
* an ACL is used to identify which traffic should be translated
	* if the source IP is **permitted** by the ACL, the source IP will be translated
	* if the source IP is **denied** by the ACL, the source IP will NOT be translated, **but the traffic will not be dropped**
* a **NAT pool** is used to define the available **inside global** addresses
* ![[./_resources/Day_45_-_NAT_(Part_2).resources/unknown_filename.1.png]]
* while being dynamically assigned, the mappings are still one-to-one (one **inside local** IP address per **inside global** IP address)
* if there aren't enough **inside global** IP addresses available - meaning all are being used - it is called **NAT pool exhaustion**
	* if a packet from another host arrives and needs NAT but there are no available addresses, the router will drop the packet
	* the host will be unable to access outside network until one of the **inside global** IP addresses becomes available
	* Dynamic NAT entries will time out automatically if not used, or you can clear them manually

**NAT Pool Exhaustion**  

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.png]]
	* if the bottom IP address tries to access the network again, and **192.168.0.167** is no longer using the network, the **100.0.0.1** address will be available again
	* **Static NAT mappings are permanent, while dynamic NAT mappings are temporary**

**Dynamic NAT Configuration**

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.1.png]]
* R1's translation table
	* this is the translation table after sending pings and some DNS traffic to 8.8.8.8
		* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.2.png]]
			
	* there are **three entries** for each mapping
		* when the router creates the **inside local to inside global** mappings the following highlighted entries are created
			* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.3.png]]
		* then the above mappings are actually used, the following highlighted entries  are made - either the **UDP** or **ICMP** entries
			* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.4.png]]
				* these udp or icmp entries will be cleared in about a minute
	* here is the output of `show ip nat statistics`
		* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.5.png]]

**PAT (Port Address Translation) - or NAT Overload**

* PAT (NAT overload) translates both the IP address and the port number (if necessary)
* by using a unique port number for each communication flow, a single public IP address can be used by many different internal hosts
	* port numbers are 16 bits, providing over 65k available port numbers
* the router will keep track of which **inside local** address is using which **inside global** address and port
* PAT is very useful for preserving public IP addresses, and is very widely used
* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.6.png]]

**PAT configuration**

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.7.png]]
	* NAT translations  
		* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.8.png]]
	* a common way to configure PAT is to  use the router's own IP address

**Command Review**

![[./_resources/Day_45_-_NAT_(Part_2).resources/image.9.png]]

**QUIZ**

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.10.png]]
	* NAT overload
		* PAT - NAT overload - allows many internal hosts to use a public IP address, because the router keeps track of communication flows using L4 port number;

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.11.png]]
	* b

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.12.png]]
	* b

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.13.png]]
	* A

* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.14.png]]
	* C
		* when an ACL is used to identify which addresses will be translated, traffic from the permitted addresses will be translated, but other address will not be translated by the router

![[./_resources/Day_45_-_NAT_(Part_2).resources/image.15.png]]

* C
	* the inside global is the external interface of the router initiating the connection
	* the inside local address is the Host initiating the connection
	* the outside local address is the host receiving the connection
	* the outside global address  is the same as the above
	* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.16.png]]
	* ![[./_resources/Day_45_-_NAT_(Part_2).resources/image.17.png]]
