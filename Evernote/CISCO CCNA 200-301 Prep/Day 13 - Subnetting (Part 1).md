---
---
![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.png]]

![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.1.png]]

**How Does a Company Get Its Own Network Address Range?**

* IPv4 addresses are assigned by the US based IANA (Internet Assigned Numbers Authority) assigns IPv4 addresses/networks  to companies based on size
	* a very large company might receive **class A** or **class B** networks, while a small company might receive a **class C** network
	* the above system led to many wasted IP addresses
		* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.2.png]]
* suppose a company needs enough IP addresses to cover 5000 end hosts
* a **class C** network won't provide enough addresses, so a **class B** network must be assigned
* as the class B network only allows for about 65.000 addresses, about 60.000 of those addresses end up being wasted

**CIDR (Class Inter-Domain Routing)**

* The creators of the internet did not realize how big it would get, resulting in flawed ways to allocate IP addresses
* the **IETF (Internet Engineering Task Force)** introduced CIDR in 1993 to replace the 'classful' addressing system
* using CIDR, the below requirements were all removed
	* Class A = /8
	* Class B = /16
	* Class C = /24
* this removal allowed larger networks to be split up into smaller networks
	* these smaller networks are called subnets

* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.3.png]]
* now, CIDR allows us to use different prefix lengths, so we're not limited to /24
	* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.4.png]]
		\-
		
	* using a /31 or /32 mask can be useful in a point-to-point situation where you don't need additional addresses but want to connect to one specific host
	* **even with subnetting, you may not be able to use a mask that provides you with the exact number of usable host addresses**

**CIDR Notation**

* the way of writing a prefix with a slash and the prefix length is called **CIDR notation,** as this style of notation was introduced with the CIDR system
* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.5.png]]

**Subnetting**

* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.6.png]]
	

**Magic Number Subnetting**

* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.8.png]]
* ![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.9.png]]
	

**QUIZ**

![[./_resources/Day_13_-_Subnetting_(Part_1).resources/image.7.png]]
