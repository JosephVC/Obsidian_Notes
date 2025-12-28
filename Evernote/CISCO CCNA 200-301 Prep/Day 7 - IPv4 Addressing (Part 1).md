---
---
**Review of Layer 3 - Network Layer**

* provides connectivity between end hosts on **different** networks
* provides logical addressing (IP addresses)
* provides path selection between source and destination
* routers operate on level 3

**Routing**

* inserting a router within a network effectively splits the network in two
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.png]]
	* the **"/24"** at the end of these IP addresses indicates which part of the IP address represents the network and which represents the end hosts (the PC); in this case the first three sections of the IP address indicate what network we're on while the last digit represents the individual PC
		* the fact that the IP address is 32 bits, the "/24" tells us to look at the first 24 bits  to find the network address and the last 8 are for the end host
	* the router needs an IP address for each network it's connected to
		* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.1.png]]

**IPv4 Addresses**

* there are 32 bits in an IPv4 address, displayed in the **dotted decimal form** shown below
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.2.png]]

* the binary number at the bottom is equal to the decimal number at the top due to how each digit in a binary number increases by a factor of two:
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.4.png]]
* the binary digits are often called **octets** and the way to **convert the octets into decimal form** is noted above, where you pay attention to each doubled value and simply add them together
* **the above pic shows that \*255\* is the largest binary digit, as we are just one digit short at a value of 254**
* **going from decimal to binary** try to subtract each binary bit's value from the decimal value, then subtract the next bit value from the previous solution, and so on:
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.5.png]]
	* here is the conversion from binary to decimal for an IPv4 address:
		* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.6.png]]
			

**Decimal and Hexidecimal**

* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.3.png]]

**IPv4 Address Classes**

* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.7.png]]
	* the end of the class A range is actually 126 rather than 127
		* the 127 range - 127.0.0.0 - 127.255.255.255 - are reserved for **loopback addresses**
		* the loopback addresses are used to test the **network stack** on the local device
			* if a device sends traffic to a loopback address, it goes up the TCP/IP stack  as if were received from another device but the traffic isn't actually going anywhere
				* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.8.png]]

**IPv4 Address Classes**

* the type of network you're working with  - whether you have many hosts to connect to or not - relates to what style of IPv4 class you'll use
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.9.png]]
	* for Class A, you have a large number of ends hosts , where in Class C you have a larger network
		* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.10.png]]
	* keep in mind the first address in the IP address is the **network address**  it can't be assigned to hosts and the **last address** of the host is the **broadcast address** - the L3 address used when you want to send traffic to all hosts - so it also cannot be assigned to hosts; the actual number of addresses ends up being two less

**Netmask**

* using a slash followed by the prefix - /24, /16, /8 - is a newer and simpler form
* CISCO devices uses a **dotted decimal netmask**
	* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.11.png]]
	* the prefixes in orange and blue actually mean the same thing, just written differently

**Network address**

* ![[./_resources/Day_7_-_IPv4_Addressing_(Part_1).resources/image.12.png]]
	* the last usable address is actually one less than the broadcast address

**QUIZ**

1.
