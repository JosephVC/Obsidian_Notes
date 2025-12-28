---
---
**what bout IPv5?**

* Internet Stream Protocol in the 1970s,
* experimental

**Hexadecimal**

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.png]]

**Binary -> Hexadecimal**

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.1.png]]

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.2.png]]
	* 0b0010    0b1111
		* 0x2    0xF
		* 0x2F

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.3.png]]
	* 0b1000    0b 0001
		* 0x8    0x1
		* 0x81

**Hex to binary**

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.4.png]]

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.5.png]]
	* 0x2    0xB
		* 0b0010    0b1011
	* 0b00101011

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.6.png]]
	* 0xD    0x7
		* 0b1101    0b0111
	* 0b11010111

**Why IPv6?**

* there simply were not enough IPv4 address available
	* given all the devices that can connect to a network, this simply isn't enough
* VLSM (Variable Length Subnet Masks), private IPv4 and NAT (Network Address Translation) have all been used to conserve the use of IPv4 address space
* IPv6 is the best long-term solution
* IPv4 address assignments are controlled by IANA
* IANA distributes IPv4 address space to various **RIRs (Regional Internet Registries)**, which then assign them to companies that need them; RIR regions are shown below
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.7.png]]

**IPv6**

* an IPv6 address is 128 bits
* using a **dual stack solution** you can add IPv6 addresses on top of preexisting IPv4 addresses
	* you keep IPv4 running and slowly transition to using IPv6
* every additional bit **doubles** the number of possible addresses
	* 2^128 is an epic shitload of IPv6 addresses compared to just over 4 billion IPv4 address
* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.8.png]]
	

**Shorting IPv6 addresses**

* **Leading 0s** can be removed
	* only the **leading** 0s are removed, but not 0s at the end of a number
		* if you remove the last 0s in a number, you'll get a completely different value once you reintroduce them
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.9.png]]
* **Consecutive quartets of all 0s** can be replaced with a double colon(::)
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.10.png]]
	* **Consecutive quartets of 0s can only be abbreviated once in an IPv6 address**
		* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.11.png]]

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.12.png]]
	

**Expanding Shortened IPv6 addresses**
![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.13.png]]

![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.14.png]]

**Finding the IPv6 prefix (global unicast addresses)**

* most enterprises requesting an IPv6 address from their ISP will received a /48 block
* typcially. IPv6 subnets us a /64 prefix length
* this means the enterprise has 16 bits to use when making subnets
* the remaining 64 bits can be used for hosts
* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.15.png]]
* to find the prefix of an IPv6 address, find the network portion and reduce the rest of the address to 0s
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.16.png]]
	* even if the prefix length is just a multiple of 4 you can use a similar strategy as the above as each hex character is 4 bits
		* reading left to right, count the number of bits in the address (shown in orange below) and add them up to the given prefix length
		* everything after this number of bits is the host portion
		* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.17.png]]
* **when the subnet mask is NOT a multiple of 4**
	* you need to
		1. count as far up to the bit value of the subnet mask,
		2. then convert the very next hex value into binary to get the very last bits you need,
		3. converting the rest of that binary value to 0s,
		4. then convert the above value back to hex
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.18.png]]

* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.19.png]]

**Configuring IPv6 Addresses**

* command **ipv6 unicast-routing**
* specify the interface
* **ipv6 address \[the address\]**
* **no shutdown**
* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.20.png]]
	* you can use a shortened or full address in configuration
* **show ipv6 interface brief**
	* there will be two IPv6 address shown with the above command, the top one being the **link-local address**
	* the link-local address is automatically configured when you manually configure an IPv6 address
	* IPv4 has link-local addresses, although they are not automatically configured

**QUIZ**

![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.21.png]]

* a, b, e
	* address C) has a G in one of its quartets, and hex numbers don't go this high up
	* D) has one too many fields
	* F) has two pairs of colons rather than one, so we have no idea how many additional quartets of 0s there might be

![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.22.png]]

* D
	* all the rest either don't shorten it enough or remove rightmost 0s rather than leading ones

![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.23.png]]

* B)
	* A) is not in **global config mode**

![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.24.png]]

* B)
	* **2001:DB8:2::/64** is the **next hop** the traffic needs to take, with **2001:DB8:1::2** being the **exit interface from RouterB**
	* ![[./_resources/Day_31_-_IPv6_(Part_1).resources/image.25.png]]
