---
---
**DHCP Snooping**

* DHCP snooping is a security feature of switches that is used to filter DHCP messages received on **untrusted** ports
* DHCP snooping only filters DHCP messages, whereas non-DHCP messages aren't affected
* all ports are **untrusted by default**
	* usually, **uplink ports** are configured as trusted ports, and **downlink** ports remain untrusted
	* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.png]]
	* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.1.png]]
* **DHCP Starvation**
	* an example of a DHCP-based  attack is a **DHCP starvation** attack
	* an attacker uses MAC addresses to flood DHCP Discover messages
	* the target's DHCP pool becomes full, resulting in a DOS to other devices
	* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.2.png]]

* **DHCP Poisoning (Man in the Middle)**
	* Similarly to ARP poisoning DHCP poisonings can be used to perform MitM attacks
	* a **spurious DHCP server** replies to clients DHCP Discover messages and assigns them IP addresses, but makes the clients use the spurious server's IP as the default gateway
		* clients usually accept the first Offer message they receive
	* this will cause the client to send traffic to the attacker instead of the legitimate default gateway
	* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.3.png]]

**DHCP Messages**

* when DHCP Snooping filters messages, it differentiates between **DHCP Server** messages and **DHCP Client** messages
* messages from **DHCP Servers**
	* OFFER
	* ACK
	* NAK = opposite of ACK, used to decline a client's REQUEST
* messages from **DHCP Clients**
	* DISCOVER
	* REQUEST
		* RELEASE = used to tell the server that the client no longer needs its IP address
			* DECLINE = used to decline the IP address offered by a DHCP server

**DHCP Snooping Operations**

* if a DHCP message is received on a **trusted port**, forward it as normal without inspection
* if a DHCP message is received on an **untrusted port**, inspect it and act as follows
	* if it is a **DHCP Server** message, discard it
	* if it's a **DHCP Client** message, perform the following checks
		* DISCOVER/REQUEST mea,
		* RELEASE/DECLINE messages: Check if the packet's source IP address and the receiving interface match the entry in the **DHCP Snooping Binding Table**; if there is  a match, forward the frame or otherwise discard it
		* when a client successfully leases an IP address from a server, create a new entry in the **DHCP Snooping Binding Table**
* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.4.png]]

**DHCP Snooping Rate-Limiting**

* DHCP snooping can limit the rate at which DHCP messages are allowed to enter an interface
* if the rate DHCP messages crosses the configured limit, the interface is err-disabled
* like with port security, the interface can be manually re-enabled, or automatically re-enabled with errdisable recovery
* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.5.png]]
* **Enabling err-disable recover for DHCP rate limiting**
	* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.6.png]]

**DHCP Option 82 (Information Option)**

* Option 82 - **dhcp relay agent information option -** is one of many dhcp options
* provides additional information about which dhcp relay agent receives the client' message, on which interface, which VLAN, etc.
* dhcp relay agents can add Option 82 to messages they forward on the remote DHCP server
* with dhcp snooping enabled, by default Cisco routers will add Option 82 to DHCP messages they receive from clients, **even if the switch isn't acting like a dhcp relay agent**
* by default, cisco switches will drop dhcp messages with Option 82 that are received on an untrusted port
* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.7.png]]
* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.8.png]]

		**QUIZ**
		
![[./_resources/Day_50_-_DHCP_Snooping.resources/image.9.png]]

* C, D, G
	* these types of messages are sent from DHCP servers, which should not be connect to untrusted interfaces

![[./_resources/Day_50_-_DHCP_Snooping.resources/image.10.png]]

* d

![[./_resources/Day_50_-_DHCP_Snooping.resources/image.11.png]]

* a, c

![[./_resources/Day_50_-_DHCP_Snooping.resources/image.12.png]]

* a, b

![[./_resources/Day_50_-_DHCP_Snooping.resources/image.13.png]]

* b

![[./_resources/Day_50_-_DHCP_Snooping.resources/image.14.png]]

* e
* ![[./_resources/Day_50_-_DHCP_Snooping.resources/image.15.png]]
