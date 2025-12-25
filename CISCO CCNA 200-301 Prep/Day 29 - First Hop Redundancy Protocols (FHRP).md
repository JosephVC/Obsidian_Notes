---
---
* **remember that subnets divide a network at Layer3 while VLANs divide a subnet at Layer 2**
	* **each subnet has its own VLAN**

* **First Hop Redundancy Protocol (FHRP)**
	* networking protocol designed to protect the default gateway on a subnetwork by allowing two or more routers to provide backup for the default gateway's particular address, usually within a few seconds.

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.png]]

* in the above example, the PCs are looking for a router with a default gateway of .254, so when that router goes down we have a problem as they don't know to try the second router
	* we need a way to get the PCs to automatically switch over to using R2, which is FHRP
* the routers get around the above problem by sending multicast Hello messages:
	* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.1.png]]
* one router will be the **active router** and be the default gateway for the network while the other router will be the **standby router**
	* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.2.png]]

**How FHRP works**

* a **virtual IP** is configured on the two routes, and a **virtual MAC** is generated for the virtual IP (each FHRP uses a different format for the virtual MAC)
* and **active** router and a **standby** router are elected (different FHRPs use different terms)
* end hosts in  the network are configured to  use the virtual IP as their default gateway
	* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.3.png]]
		
* the active router replies to an **ARP reply** using the virtual MAC address, so traffic destined for other networks will be sent to it
	* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.4.png]]
		
* if the active router fails, the standby becomes the next active router
	* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.5.png]]
		
	* the new active router will send **gratuitous ARP messages** so that switches will update their MAC address table; it now functions as the default router
		* **gratuitous ARP -** ARP replies sent without being requested (no ARP request message was received); the frames are broadcast to FFFF.FFFF.FFFF (normal ARP replies are unicast)
		* ![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.6.png]]
			
* if the old active router comes back online it becomes the standby router
	* FHRPs are **non preemtive,** meaning the current active router will not automatically give up its role, even if the former active router returns
	* you can configure 'preemption' so that the old active router does take back its old role

**Hot Standby Router Protocol (HSPR )**

* Cisco proprietary
* an active and standby router are elected
* there are two versions: v1 and v2
	* v2 adds IPv6 support and increases the number of groups that can be configured
* **multicast IPv4 address**
	* v1 = 224.0.0.2
	* v2 = 224.0.0.102
* **Virtual MAC address**
	* v1 = 0000.0c07.acXX (XX = HSRP group number)
	* v2 = 0000.0c9f.fXXX (XXX = HSRP group number)
* in a situation with multiple subnets/VLANs, you can configure a different active router in each subnet/VLAN to load balance

**Virtual Router Redundancy Protocol (VRRP)**

* open standard
* a **master** and **backup** router are elected
* multicast IPv4 address: 224.0.0.18
* virtual MAC address: 0000.5e00.01XX (XX = VRRP group number)
* in a situation with multiple subnets/VLANs, you can configure a different master router in each subnet/VLAN to load balance

**Gateway Load Balancing Protocol (GLBP)**

* Cisco proprietary
* Load balances among multiple routers **within a single subnet**
* an **Active Virtual Gateway (AVG)** is elected
* up to four **Active Virtual Forwarders (AVFs)** are assigned by the AVG (the AVG itself can be an AVF, too)
* each AVF acts as a default gateway for a portion of the hosts in the subnet
* Multicast IPv4 address:  224.0.0.102
* Virtual MAC address:  0007.b400.XXYY (XX = GLBP group number, YY = AVF number)

**Configuring HSRP**

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.7.png]]

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.8.png]]

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.9.png]]
**QUIZ**

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.10.png]]

* d)

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.11.png]]

* a)

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.12.png]]

* b), d)

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.13.png]]

* gratuitous ARP

![[./_resources/Day_29_-_First_Hop_Redundancy_Protocols_(FHRP).resources/image.14.png]]

* C)
