---
---
ARP Review

* ARP is used to learn the MAC address of another device with a known IP address
* as an example, a PC will use ARP to learn the MAC address of its default gateway to communicate with external networks
* typically it is a two message exchange, a **request** and a **reply**
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.png]]
* **the actual ARP request**
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.1.png]]
* **The ARP reply**
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.2.png]]
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.3.png]]
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.4.png]]
* **Gratuitous ARP**
	* a gratuitous ARP message is an ARP reply that is sent without receiving an ARP request
	* it is sent to the broadcast MAC address
	* allows other devices to learn the MAC address of the sending device without having to send ARP requests
	* some devices send GARP messages when an interface is enabled, IP address is changed, MAC address is changed, etc.
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.5.png]]

**Dynamic ARP Inspection**

* DAI is a security feature of switches that is used to filter ARP messages received on **untrusted** ports
* DAI only filers ARP messages while non-ARP messages aren't affected
* **all ports are untrusted by default**
	* typically, all ports connected to other network devices (switches, routers) should be configured as **trusted** while interfaces connected to end hosts should remain **untrusted**
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.6.png]]

**ARP Poisoning (MitM)**

* like DHCP poisoning, ARP poisoning involves an attacker manipulating target's ARP tables so traffic is sent to the attacker
* an attacker can send gratuitous ARP messages using another device's IP address
* other devices in the network will receive the GARP and update their ARP tables, causing them to send traffic to the attacker instead of the legitimate destination
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.7.png]]

**Dynamic ARP Inspection Operations**

* DAI inspects the **sender MAC** and **sender IP** fields of ARP messages received on **untrusted** ports and checks that there is a matching entry in the **DHCP** **snooping binding table**
	* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.8.png]]
	* if there is a matching entry, the ARP message is forwarded automatically
	* if there isn't  matching entry, the ARP message is discarded
	* DAI doesn't inspect messages received on **trusted** ports; they are forwarded as normal
	* **ARP ACLs** can be manually configured to map IP address/MAC addresses for DAI to check
		* useful for hosts that don't use DHCP
	* DAI can be configured to perform more in-depth check also
	* like DHCP snooping, DAI also supports rate-limiting to prevent attackers from overwhelming the switch with ARP messages
		* both DHCP snooping and DAI require work by the switch's CPU, which can be overloaded with ARP messages (even though they are blocked)

**DAI configuration**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.9.png]]
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.10.png]]

**DAI Rate Limiting**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.11.png]]

**DAI Optional Checks**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.12.png]]
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.13.png]]
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.14.png]]

**ARP ACLs**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.15.png]]
* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.16.png]]

![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.17.png]]

**QUIZ**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.18.png]]
	* A

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.19.png]]
	* C
		* for all the configurations to be valid, they needed to be all configured on a single line, as by default **only the last command entered will take affect**

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.20.png]]
	* B, D

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.21.png]]
	* B, D
		* when DHCP snooping is enabled, the DHCP binding table is built automatically as hosts lease IP addresses; DAI uses that table to check ARP messages
		* ARP ACLs can be manually configured to permit the ARP messages of those hosts  that don't use DHCP

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.22.png]]
	* A, C
		* 45 packets over 3 seconds allows for short bursts at a higher rate - such as 30/15/0 packets

![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.23.png]]

* B, E

* ![[./_resources/Day_51_-_Dynamic_ARP_Inspection.resources/image.24.png]]
