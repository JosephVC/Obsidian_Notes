---
---
**Native VLAN feature on a router**

![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.png]]

* best practice is to set the native vlan to an **unused VLAN, for security purposes**, but if you want to use the native VLAN it's important how to do so on a router
	* because frames in the native VLAN are not tagged, it can send more frames per second as each frame is smaller
* there are two methods of configuring a native VLAN on a router
	* use the command `encapsulation dot1q [vlan id] native` on the router subinterface
		* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.1.png]]
			
	* the command `ip address [desired IP address]` to configure the IP address for the native VLAN on the router's physical interface (the above command is not necessary)

**Layer 3 (Multilayer) Switches**
![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.2.png]]

* Layer 3 switches are also called multilayer switches
* a **multilayer switch** is capable of both switching and routing
* is **layer 3 aware**
	* an L2 switch is not L3 aware but only cares about L2 information like MAC addresses
	* being L3 aware means the switch takes into consideration IP addresses and routing
* you can assign IP addresses to its interfaces, like a router
	* you can configure **routed ports** on a L3 switch
	* you can create virtual interfaces for each VLAN, and assign IP addresses to those interfaces
* route can be configured, as if on a regular router
* L3 switches can be used for inter-VLAN routing
	* one way for inter-VLAN routing is using one connections for each VLAN for each router and switch
		* if you have a great deal of VLANs, you may not have enough interfaces on your router
		* **router on a stick (ROAS)** is another method of inter-VLAN routing, where VLANs are routed through a single trunk connection
			* this is efficient in terms of preserving available interfaces, but can lead to congestion if the network gets busy

**Inter-VLAN Routing via SVI**

![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.3.png]]

* **Switch Virtual Interfaces (SVIs)** are the virtual interfaces you assign IP addresses to in a multilayer switch
* configures each PC to use the SVI - **not the router -** as their gateway address
	* when using ROAS, the router was the PC gateway, but we now use the switch's SVIs instead
* to send traffic to a different subnet/VLAN, the PC will send traffic to the switch, and the switch will route the traffic
* **Router Configurations**
	* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.4.png]]
		* use the `no interface [some interface]` command to delete the previous interfaces
		* reset your selected interface using `default interface [some interface]`
		* use `do show ip interface brief` to check the status of the interfaces
		* use `interface [selected interface]` to set up that particular interface
		* set up the IP address for that interface
		* go back and use `do show ip interface brief` to re-check the status of the interface
* **Switch Configuration**
	* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.5.png]]
		* **THE COMMAND `ip routing` ENABLES LAYER 3 ROUTING ON THE SWITCH.  YOU NEED TO USE IT.**
* **Configure the default route**
	* `ip route 0.0.0.0 0.0.0.0 [the IP address of the next hop]`
* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.6.png]]
* **creating an SVI for a VLAN that does not exist**
	* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.7.png]]
	* note that in the above, the status is down as there has been no VLAN40 set up on the switch
* **how to ensure an SVI will be completely UP**
	1. The VLAN must exist on the switch
	2. the switch must have at least one access port on the VLAN in an up/up state, **AND/OR** one trunk port that allows the VLAN that is in an up/up state
	3. the VLAN must not be shutdown - the VLAN can be disabled with the `shutdown` command

* this can't be done in Packet Tracer but will likely require a real switch

4.      the SVI itself must  not be shutdown (SVIs are disabled by default)

**QUIZ**

1. ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.8.png]]

* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.9.png]]

2. ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.10.png]]

* either the VLAN225 does not exist and/or VLAN225 does not have any interfaces that are up/up

3. which command is used to configure a switch interface on a routed port?

* `no switchport`

**CCNA PRACTICE QUESTION**

* ![[./_resources/Day_18_-_VLANs_(Part_3).resources/image.11.png]]
	* VLAN 44 traffic is untagged because it is configured as the native VLAN by the `switchport trunk native vlan 44` command
