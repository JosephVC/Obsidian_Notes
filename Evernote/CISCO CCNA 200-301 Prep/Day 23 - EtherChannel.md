---
---
This lecture covers exam topic 2.4 - Configure and verify (Layer 2/3) EtherChannel (LACP)

![[./_resources/Day_23_-_EtherChannel.resources/image.png]]

Adding more links does not necessarily solve the problem

![[./_resources/Day_23_-_EtherChannel.resources/image.1.png]]

* if  you connect two switches together **with multiple links**, all except one will be **disabled** by spanning tree
* if all of ASW1's interfaces were forwarding, L2 loops would form between ASW1 and DSW1, leading to broadcast storms
* other links will be unused unless the active link fails; in that case, one of the inactive links will start forwarding

**EtherChannel**

![[./_resources/Day_23_-_EtherChannel.resources/image.2.png]]

* EtherChannel groups multiple interfaces together to act as a single interface
* STP will treat this group as a single interface
	* no loop will form because this group of interfaces will **act as if** they are a single link
* ![[./_resources/Day_23_-_EtherChannel.resources/image.3.png]]
	* While PC1 sends a frame to ASW1, and ASW1 sends copies of the frame back to the other connected PCs
	* DSW1 only receives one copy of the frame, as EtherChannel makes the four physical interfaces act as one logical interface
	* traffic using the EtherChannel will be **load balanced** among the physical interfaces in the group.  an algorithm is used to determine which traffic will use which physical interface
	* Now, DSW1 will forward the frame out of all other interfaces, **except** the one it received the frame on.  So, all the other interfaces **but** the ones grouped together under EtherChannel because this interface behaves as a single interface
* Some other names for EtherChannel are
	* Port Channel
	* LAG (Link Aggregation Group)

**EtherChannel Load Balancing**

![[./_resources/Day_23_-_EtherChannel.resources/image.4.png]]

* EtherChannel load balances based on **flows**
	* a flow is a communication between two nodes in the network
	* different physical interfaces in the EtherChannel will be used for different flows
* frames in the same flow will be forwarded using the same physical interface
	* if frames in the same flow were forwarded using different physical interfaces, some frames may arrive at the destination out of order, which can cause problems; some applications deal with out-of-order frames better than others
* the calculation to determine which physical interface to use takes into account several inputs
	* you can change the inputs used in the interface selection calculation
	* **inputs that can be used**
		* Source MAC
		* Destination MAC
		* Source MAC **and** Destination MAC
		* Source IP
		* Destination IP
		* Source **and** destination IP
* **load balancing channels**
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.5.png]]
	* `show etherchannel load-balance`
	* `port-channel load-balance [method]`

**EtherChannel Configuration**

![[./_resources/Day_23_-_EtherChannel.resources/image.13.png]]

* there are three methods of EtherChannel configuration on Cisco switches
	* **Port Aggregation Protocol (PAgP)**
		* Cisco proprietary protocol
		* dynamically negotiates the creation/maintenance of the EtherChannel (like DTP for trunks)
	* **Link Aggregation Control Protocol (LACP)**
		* Industry standard protocol (IEEE 802.3ad)
		* Dynamically negotiates the creation/maintenance of the EtherChannel (like DTP for trunks)
		* **this is the preferred method of configuring EtherChannels**
			* **noted in section 2.4 of CCNA exam guide**
	* **Static EtherChannel**
		* A protocol isn't used to determine if an EtherChannel should be formed
		* interfaces are statically configured to form an EtherChannel
	* **up to 8 interfaces** can be formed into a single EtherChannel (LACP allows up to 16, but only 8 will be active, the other 8 will be in standby mode, waiting for an active interface to fail)

**PagP Configuration**

* ![[./_resources/Day_23_-_EtherChannel.resources/image.6.png]]
* ![[./_resources/Day_23_-_EtherChannel.resources/image.7.png]]
	* the `channel group` command is used to configure the **EtherChannel**, but the name of the **virtual interface created** is **port-channel**
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.8.png]]

**LACP Configuration**

* largely the same as above, but certain terms have changed:
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.9.png]]

**Static EtherChannel Configuration**

* ![[./_resources/Day_23_-_EtherChannel.resources/image.10.png]]
	* note that there is only one mode, **on**, which tells interfaces to form an EtherChannel
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.11.png]]

**Manually Configure the Negotiation Protocol**

* ![[./_resources/Day_23_-_EtherChannel.resources/image.12.png]]
	* `show running config` displays the status of the physical interfaces
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.14.png]]
		* these physical interfaces were not manually designated as trunks
		* the trunk configurations which were configured on the port-channel interface were also applied to the physical interfaces

**Other EtherChannel Configuration issues**

* Member interfaces must have matching configurations
	* same duplex
	* same speed
	* same switchport mode (access/trunk)
	* same allowed VLANs/native VLAN (for trunk interfaces)
* if an interface's configurations do not match the others, it will be excluded from the EtherChannel

**Verify EtherChannel Status**
`show etherchannel summary`
![[./_resources/Day_23_-_EtherChannel.resources/image.15.png]]
now port channel 1 is shutdown:

* ![[./_resources/Day_23_-_EtherChannel.resources/image.16.png]]

now an interface is in access mode:

* ![[./_resources/Day_23_-_EtherChannel.resources/image.17.png]]
	* here, one interface is **suspended** while the other three are still active
* `show etherchannel port-channel`
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.18.png]]
* `show spanning-tree`
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.19.png]]

**Layer 3 EtherChannel**
![[./_resources/Day_23_-_EtherChannel.resources/image.20.png]]

* note the use of multi-layer switches
* modern networking often leans toward using L3 connections between switches, so STP won't be an issue
	* suppose you had 4 switches connected in a mesh; as long as they were connected with L3 routed ports all their interfaces would be up and forwarding and none will have to be disabled due to spanning tree
* even with EtherChannel, the below diagram could still be subject to a broadcast storm
	* ![[./_resources/Day_23_-_EtherChannel.resources/image.21.png]]
	* STP would block one of these interfaces, like so:
		* ![[./_resources/Day_23_-_EtherChannel.resources/image.22.png]]
	* but if all the above connections were made with routed ports rather than L2 switch ports **there is no need to run STP at all**
		* routed ports don't forward L2 broadcasts so no L2 loops can be formed

**Configuring a L3 EtherChannel**

* ![[./_resources/Day_23_-_EtherChannel.resources/image.23.png]]

**Commands**

![[./_resources/Day_23_-_EtherChannel.resources/image.24.png]]

**QUIZ**

![[./_resources/Day_23_-_EtherChannel.resources/image.25.png]]

* on - on
* desirable - auto
* active - active

![[./_resources/Day_23_-_EtherChannel.resources/image.26.png]]

* the interfaces are bundled in the port-channel

![[./_resources/Day_23_-_EtherChannel.resources/image.27.png]]

* interface speed
* switchport mode

**Boson-Exim practice Question**

* ![[./_resources/Day_23_-_EtherChannel.resources/image.28.png]]
	* no link will be formed
		* as LACP was configured in the first set of commands, the `channel-group 1 mode on` command would be rejected because the only modes you can configure in this context are **active** and **passive**
		* same regarding PAGP![[./_resources/Day_23_-_EtherChannel.resources/image.29.png]]
