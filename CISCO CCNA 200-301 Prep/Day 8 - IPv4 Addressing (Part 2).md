---
---
**Maximum Hosts Per Network**

* if using a Class C address (/24), you are saying there can be a maximum number of hosts per network; these range from 0 to 255 or **254 possible hosts**
	* host portion = 8 bits = 2^8 = 256
	* remove two for the sake of the **network address** (host portion is all 0s) and the **broadcast address** (host network is all 1s)
* if using a Class B address (/16), there can be a maximum of **65,534** host addresses
	* Host portion = 16 bits = 2^16 = 65, 536
	* remove two for the sake of the network address and the broadcast address
* if using a Class A address (/8) you have a maximum of 16, 777, 214 hosts
	* host portion = 24 bits = 2^24 = 16.777.216
	* remove two for the sake of the network address and broadcast address
	* **maximum hosts per network = 2^n - 2 (=number of host bits)**

**First/Last Usable Address**

* add 1 to the network address to the **first usable address**
* remove 1 from the network address to get the **last usable address**
* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.png]]

**IPv4 Addressing**

* the command s**how ip interface brief** allows us to confirm the status of each item on the network
	* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.1.png]]
	* if **status** shows administratively down then the interface has been disabled with the shutdown command
	* this is the default status of CISCO **router** interfaces
	* CISCO **switch** interfaces are NOT administratively down by default
	* **status** refers to the L1 (are all the relevant cables connected), the **Protocol** L2 (is the device functioning properly)
* **Configuring interfaces**
	* remember to input **conf t**
	* enter some variant of interface gigabitethernet 0/0
		* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.2.png]]
		* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.3.png]]
		* if you simply type **show interfaces \[some interface\]** you get large volume of information
			* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.4.png]]
				* the term bia refers to the **burned in address** or the MAC address
					* the reason the MAC address is listed twice is that bia stands for the actual MAC address, but you can configure a different MAC address with in the CLI
		* typing show interfaces description you receive the following screen
			* ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.5.png]]
			* the **interface description** are optional but helpful in specifying the purpose of each interface

**QUIZ**

1. ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.6.png]]

2. ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.7.png]]
	

3. ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.8.png]]

4. ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.9.png]]

5. ![[./_resources/Day_8_-_IPv4_Addressing_(Part_2).resources/image.10.png]]
6.
