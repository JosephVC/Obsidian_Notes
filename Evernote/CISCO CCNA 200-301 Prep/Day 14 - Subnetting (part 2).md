---
---
![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.png]]
**figuring this out**

1. to find the broadcast address of subnet 1, change the binary representation of the last octet to all 1s, which ultimately gives you 192.168.1.63
2. the network address will be **one higher than the previous broadcast address**, or **192.168.1.64**
3. the broadcast address for subnet 2 is 192.168.1.127, so the **network address for subnet 3 is 192.168.1.128**
	* the final octet of the subnet 3 is 1 0 0 0 0 0 0 0, to so get the broadcast address of subnet 3 change this binary representation to all 1s (1 0 1 1 1 1 1 1- **keep in mind the /26 network mask, so we have two fewer host bits to consider** - which gives us a broadcast address of 192.168.1.191

4\. knowing subnet 3's broadcast address we get the network address of subnet 4 by adding 1 to the last number, giving us the **network address of subnet 4 = 192.168.1.192**
![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.1.png]]

**Subnetting Tricks**

* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.2.png]]
	* note that with a /26 subnet mask, the network portion starts with 64, and with every new subnet you can simply add 64 to the previous

**Subnetting**

* in a network with a /24 mask, we're in a situation where we can't borrow any bits and thus can't create any subnets
	* we just have one network in the below example
		* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.3.png]]
			
* with a /25 mask, we can borrow one bit and **we can make two subnets**
	* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.4.png]]
		

**FORMULA FOR ESTABLISHING SUBNETS**

* **2^x (x = number of 'borrowed' bits)**
	* so, with a /25 mask, you are borrowing one bit, so the formula is 2^1 = 2 possible subnets

**When we borrow bits to make a larger mask, we are expanding the network portion,  not the host portion**

![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.5.png]]

* the above example leaves out three possible subnets:
	* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.6.png]]

**Identifying the Subnet**

* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.8.png]]

1. get the address in binary
2. look at the subnet mask to find where the network part ends (here, we're borrowing five bits)
3. convert those relevant network bits to decimal
	* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.7.png]]

**Subnet Hosts - Class C**

![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.9.png]]

* note the two possible addresses when using a /31 subnet mask - this is for establishing a point to point connection where the two possible addresses are for either end of the connection (there is no network or broadcast addresses)
* the /32 mask would be appropriate when writing a route for a single specific host

**Subnetting Class B networks**

* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.10.png]]
	* /23 gives us 128 subnets, which does waste a few

* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.11.png]]
	* you would need a /25 subnet

* ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.12.png]]
	* you would need  /24 subnet

![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.13.png]]
172.25.\[ 11011001 \] . \[ 11000000 \]
172.25.216.0

![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.14.png]]

**QUIZ**

1. ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.15.png]]
	* A /23 subnet

2.  
![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.16.png]]

* 172.21. 0**1101**111   .0 - the /20 network mask borrows 4 bits from the regular /16 mask, so going from left to right we calculate the decimal equivalent of the first four bits
	* 172.21.96.0

3. ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.17.png]]
	* **192.168.91.127** (the binary representation of the last octet is 01001110 - we borrow two bit from the last octet **but also change the rest of the six remaining host bits to 1 - 01111111 -** which gives us the decimal value of 127)

4. ![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.18.png]]
	* to get 4 subnets you need a network mask of /18
	* a /18 mask means you take two bits from the third octet
	* converting the remaining host bits to 1s gives you the broadcast address of the second address : 172.16.127.255
		

5 .
![[./_resources/Day_14_-_Subnetting_(part_2).resources/image.19.png]]

* per the table above, you would have 64 subnets with a prefix length of /22
* as you borrow 6 bits , 2^6 gives you 64 subnets you can make
