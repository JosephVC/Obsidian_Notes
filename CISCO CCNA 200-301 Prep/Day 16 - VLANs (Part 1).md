---
---
**What is a LAN?**

* a group of devices in a single location
* a **single broadcast domain**, including all devices in that broadcast domain
	* a **broadcast domain** is the group of devices which will receive a **broadcast frame** (destination MAC FFFF.FFFF.FFFF) sent by any one of its members
		* a router will receive a broadcast frame but not forward it to other networks

**LANs/Broadcast Domains**

* there are 4 different broadcast domains in the picture below
	* ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.png]]
		

**What is a VLAN?**

* **VLANs** are configured on switches on a **per-interface** basis
* VLANs logically separate end hosts on L2
* Performance - lots of necessary broadcast traffic can reduce network performance
* Security - hosts on a single network can still talk to each other without passing through a router, so the security config on the router won't necessarily be applicable
	* to better secure the network, separate hosts into separate subnets so that security policies will apply
		* connect each subnet separately to the router:
			* ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.1.png]]
				* the above is not necessarily the most efficient way to securely connect the subnets
					* either you are forcing all traffic through the router before it goes anywhere else, or if the **frame from PC1 is a broadcast or unicast frame, the switch will flood the network, reducing performance**
				* while the above subnets are separate on L3, they are still on the same L2 broadcast domain
					* we use **Virtual LANs (VLANs) to separate the LANs at L2**
					* a switch will **not forward traffic between VLANs, including broadcast/unicast traffic**
					* the switch **does not perform inter-VLAN routing (one VLAN to another), but must send traffic through the router**

VLAN Configuration

* **show vlan brief** is the command to display your VLAN status
* **interface range \[the interface range\]** allows you to configure a range of interfaces at once
* the **switchport mode access** command allows you to **configure** the interface as an **access port**
	* an **access port** is a switchport which belongs to a single VLAN, and usually connects to end-hosts like PCs
	* switchports that carry multiple VLANs are called **trunk ports**
* **switchport access vlan \[particular port\]** configures the VLAN of a switch access port and assigns the VLAN to a particular port; you should always specify which VLAN you're working on rather than let the terminal guess
* **VLANs 1, 1002-1005 exist by default and** **cannot be deleted**
* `**vlan [vlan number]**`creates a VLAN
* ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.2.png]]

**The default VLAN Cisco switches are in is VLAN1**

**QUIZ**

1. ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.3.png]]
	* 6 domains, including that between the routers

2. ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.4.png]]
	* 5 broadcast domains, including between the routers

3. What happens when  you try to assign a switch interface to a VLAN that does not exist?
	* the switch will create the VLAN
	* ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.5.png]]

4. ![[./_resources/Day_16_-_VLANs_(Part_1).resources/image.6.png]]
	* 3 devices will receive it
		* the switch, which will send the packet out of all interfaces in VLAN20
		* the router
		* the destination computer
	* **if no VLANs were configured, then the network would be flooded**

5. You create VLANs 10, 20, and 30 on a CISCO switch.  How many VLANs will be displayed in the output of the show vlan brief command
	* 8, including VLANs 1 and 1002-1005
