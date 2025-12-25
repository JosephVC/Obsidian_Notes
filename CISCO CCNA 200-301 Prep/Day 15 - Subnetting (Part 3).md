---
---
the process of subnetting class A, B, or C is all exactly the same

**Subnetting Class A Networks**

* ![[./_resources/Day_15_-_Subnetting_(Part_3).resources/image.png]]
	* using the formal 2^x, where the x is the number of host bits borrowed, we need to borrow 11 bits (2^11 = 2048 subnets)
	* borrowing 11 bits gives us a **/19** prefix
	* so, the regular /8 subnet mask gives us an address field of 255.0.0.0
		* 11111111.00000000.00000000.00000000
	* borrowing 11 bits gets us the following binary representation of 255.255.224.0
		* 11111111.11111111.11100000.00000000
		* we have 13 remaining host bits to work with
		* to get the number of usable addresses we use the equation (2^n) - 2, where n is the number of host bits
			* (2^13)  - 2 = 8190

![[./_resources/Day_15_-_Subnetting_(Part_3).resources/image.1.png]]

1. 10\. \[11011001\] 192.0.0/11
2. 10\. \[11011111\] 223.255.255/11
3. add one to the network address = 10.192.0.0/11
4. subtract one from the broadcast address = 10.223.255.254/11
5. 2^n (n= host bits) -2
	* we have 21 host bits, so (2^21) - 2 = 2,097,150 hosts per subnet

**VLSM - Variable Length Subnet Masks**

* all the above subnets have FLSM (Fixed Length Subnet Masks)
	* all the subnets use the same prefix length (such as subnetting a class C network into 4 subnets using /26)
* **VLSM** is the process of creating subnets of different sizes to make your use of network addresses more efficient

1. Assign the largest subnet at the start of the address space
2. Assign the second-largest subnet after it
3. repeat the process until all subnets have been assigned

![[./_resources/Day_15_-_Subnetting_(Part_3).resources/image.2.png]]

1. using the formula 2^x, where x is the number of host bits we need, 2^7 = 128, just over the amount we need
	* we borrow one host bit from the last octet, so the network address is **192.168.1.0/25**

2\. **192.168.1.127** is the broadcast address
3   the first usable address will be **192.168.1.128/25**

4. the last usable address will be **192.168.1.126/25**
5. (2^7) - 2 = 126 usable host addresses

**THE NETWORK ADDRESS OF THE NEXT SUBNET IS 1 ADDED TO THE LAST OCTET IN THE PREVIOUS SUBNET'S BROADCAST ADDRESS**

**Toronto LAN B**
**192.168.1.00000000**
we need 6 host bits to get 62 usable host addresses so our prefix will be /26

* ![[./_resources/Day_15_-_Subnetting_(Part_3).resources/image.3.png]]
	* to find the network address we set all the host bits to 0

1. the network address is 192.168.1.128/26   
2. the broadcast address is 192.168.1.191/26
3. the first usable address is 192.168.1.192/26
4. the last usable address is 192.168.1.190/26

**Toronto LAN A**
**192.168.1.00000000**
**192.168.1.10000000**
**our prefix will be /27 as we borrow 3 host bits**

1. **the** network address is 192.168.1.192/27
2. the broadcast address is 192.168.1.223/27
3. the first usable address is 192.168.1.193/27
4. the last usable address is 192.168.1.222/27
5. number of usable addresses is 30

Tokyo LAN B
192.168.1.11101111

1. network address is 192.168.1.224/28
2. broadcast address is 192.168.1.239/28
3. the first usable address is one added to the network address = 192.168.1.225/28
4. the last usable address is one subtracted from broadcast address = 192.168.1.238/28
5. the number of usable addresses is 14

**Point to Point connection**

**.00000000/30**
**.11110000**

1. **network address** is 192.168.1.240/30
2. broadcast address is 192.168.1.243/30
3. first usable address is one added to the network address = 192.168.1.241/31
4. the last usable address is subtracted from the broadcast address = 192.168.242/31
5. there are 2 usable addresses
