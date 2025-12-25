---
---
**Private IPv4 Addresses (RFC 1918)**

* IPv4 does not provide enough addresses for all the devices that need them
* it's no small thing to switch devices from using IPv4 to IPv6
* there are three short-term solutions
	* CIDR
	* Private IPv4 addresses
	* NAT
* RFC 1918 provides the following range of private IPv4 addresses
	* 10.0.0.0/8 (10.0.0.0 to 10.255.255.255) - Class A
	* 172.16.0.0/12 (172.16.0.0 to 172.31.255.255) - Class B
	* 192.168.0.0/16 (192.168.0.0 to 192.168.255.255) - Class C
	* **CIDR makes address classes a thing of the past**
* **Private IPv4 addresses cannot be used over the Internet**
* with private IPv4 addresses, you can run into two problems NAT can solve
	* duplicate addresses
	* PCs with private addresses can't even access the internet with their addresses
* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.png]]

**Network Address Translation (NAT)**

* NAT is used to modify the source and/or destination IP addresses of packets
* a common reason to use NAT is that it allows hosts with private IP addresses to communicate with other hosts over the internet
* for the CCNA you need to  understand **source NAT** and how to configure it on Cisco routers
	* per the below graphic, source NAT translates the source IP address into the IP address of the given router's external interface
	* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.1.png]]

**static NAT**

* static NAT statically configures one-to-one mappings of private IP addresses to public IP addresses
* an **inside local** IP address is mapped to an **inside global** IP address
	* **inside local:** the IP address of the **inside host**, from the perspective of the local network
		* this is the IP address actually configured on the inside host, usually a private address
	* **inside global:** the IP address of the **inside host**, from the perspective of the **outside hosts**
		* this is the IP address of the inside host **_after NAT_**,  usually a public address
	* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.2.png]]
		* **you cannot map _both_ PC1 and PC2 to the reconfigured 100.0.0.1 address**
* while static NAT allows devices with private IP addresses to communicate over the internet, the need to do a one-to-one mapping doesn't help preserve IP addresses

**Static NAT Configuration**

* keep in mind that you **need to own a public IP address** in order to use it
* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.3.png]]

**show ip nat translations**

* **outside local:** the IP address of the **outside** host, from the perspective of the **local network**
* **outside global:** the IP address of the **outside** host, from the perspective of the **outside network**
* unless **destination NAT** is used, these two addresses will be the same
* **inside/outside** \= location of the host whether on the inside or outside network
* **local/global** = perspective, whether from the local, inside network or from the perspective of the global, outside network

**clear ip nat translation**

* clear all the dynamic NAT translations
* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.4.png]]

**Command Review**

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.5.png]]

QUIZ

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.6.png]]
	* d
		* only d has the proper command and the IP addresses in the right order-

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.7.png]]
	* B
		* you can't have two addresses translated to a single address at the same time
			* the second command to translate the address will be rejected
			* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.8.png]]

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.9.png]]
	* B
		\- the command only clears the **dynamic** translation
		

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.10.png]]
	* a, e, f

* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.11.png]]
	* Outside global: 8.8.8.8
	* outside local: 8.8.8.8
	* inside local: 172.20.0.101
	* inside global: 200.0.0.1

![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.12.png]]

* F is the IP address of HostA
* ![[./_resources/Day_44_-_Network_Address_Translation_(NAT).resources/image.13.png]]
