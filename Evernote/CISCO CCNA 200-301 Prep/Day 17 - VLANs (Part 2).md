---
---
![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.png]]

**Trunk Ports**

* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.3.png]]
	
* in a small network with few VLANs, it is possible to use a separate interface for each VLAN when connecting switches to switches, and switches to routers
	* this is not viable when the number of VLANs increases; this will result in wasted interfaces and often routers won't have enough interfaces for each VLAN
	* **trunk ports** are meant to carry multiple VLANs over a single interface
		* the trunk port is not an access port, which belongs to only one VLAN
* **VLAN tagging -** VLANs will 'tag' all frames that they send over a trunk link.  this allows the receiving switch to know which VLAN the frame belongs to
	* **trunk ports -** 'tagged' ports
	* **access ports -** 'untagged' ports

**VLAN Tagging**

* **there are two main trunking protocols: ISL (Inter-Switch Link) and IEEE 802.1Q (dot1q)**
	* ISL is an old Cisco proprietary protocol created before the industry standard 802.1Q
		* this protocol would be rarely encountered in a modern system
	* IEEE 802.1Q is the current industry standard

**Ethernet Frame**

* the dot1q tag is inserted between two fields of the ethernet header
* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.1.png]]

**802.1Q Tag**

* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.2.png]]
	
* inserted between the **Source** and **Type/Length** field
* the tag is 4 bytes (32 bits)
* The tag consists of two main fields
	* **Tag Protocol Identifier (TPID)**
		* 2 bytes (16 bits) in length
		* always set to a value of 0x8100; this indicates the frame is 802.1Q
			* 0x = hexadecimal value
	* **Tag Control Information (TCI)**
		* **Priority Code Point (PCP)**
			* 3 bits in length
			* used for Class of Service (COS), which prioritizes important traffic in congested networks
		* **Drop Eligible Indicator (DEI)**
			* 1 bit in length
			* used to indicate frames that can be dropped if the network gets congested
		* **VLAN ID (VID)**
			* 12 bits in length
			* the field that actually identifies the field the VLAN belongs to
			* 2^12 = 4096 possible VLANs with a range of 1-4094 **usable** VLANs
				* 0 and 4095 are reserved and can't be used

**VLAN Ranges**

* the 1 - 4094 usable VLAN range is divided into two sections
	* normal VLANs : 1 - 1005
	* extended VLANs: 1006 - 4094
* some older devices can't use the extended VLAN range, but most modern devices should be able to support the extended VLAN range

**Native VLAN**

* 802.1Q has a feature called **native VLAN** (which ISL does not have)
* the native VLAN is VLAN1 by default on all trunk ports, but this can be manually configured
* the switch does not add an 802.1Q tag to frames in the native VLAN
* when the switch receives an untagged frame on the trunk port, it assumes the frame belongs to the native VLAN.  **it is very important that the native VLAN matches**
	* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.4.png]]

**Trunk Configuration**

* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.5.png]]
	
* to configure a trunk port, start by entering `interface g0/0` (or whatever other interface you want to work on)
* then use the command `switchport mode trunk` to manually configure the interface as a trunk
* many modern switches do not support ISL but only dot1q
* what switches support both protocols  have a trunk encapsulation of 'Auto' by default
	* you must thus first set the encapsulation to dot1q or ISL, unless the switch only supports dot1q, in which case this explicit setting is not necessary
* after you set the encapsulation type, you can then configure the interface as a trunk
* `switchport trunk encapsulation ?`  will give you the available options on the switch
	* the `negotiate` option sets encapsulation to 'Auto' so we may not be able to use that
* after you find the supported encapsulation you want to use, `switchport trunk encapsulation dot1q` will set the encapsulation to dot1q
* now `switchport mode trunk` is accepted
* \`do show interfaces trunk\` 
* `do show interfaces trunk`  command will confirm what encapsulation is being used
	* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.6.png]]
* `switchport trunk allowed vlan ?` is the command to configure the VLANs allowed on a trunk
* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.7.png]]
* for security purposes, it is best to change the native VLAN to an **unused VLAN - make sure the VLAN matches on both switches**
* `switchport trunk native vlan [vlan number]` **is the command to change the native VLAN**
* `show vlan brief` will give you an overview of your VLAN
	* this command shows the access ports assigned to each VLAN, **not** the trunk ports that allow each VLAN
	* use `show interfaces trunk` to confirm trunk ports

**full set of commands to configure a trunk**

![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.8.png]]

**Router on a Stick (ROAS)**

* used to route between multiple VLANs using a single interface on the router and the switch
* the switch interface is configured as a regular trunk
* the router interface is configured using **subinterfaces**; you configure the VLAN tag and IP address  on each subinterface
* the router will behave as if frames arriving with a certain VLAN tag have arrived on the subinterface configured with that VLAN tag
* the router will tag frames sent out of each subinterface with the VLAN tag configured on the subinterface
* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.9.png]]
	* while there is a single connection to the router, but that connection hosts three virtual connections:
		* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.10.png]]
	* ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.11.png]]

**QUIZ**

1. ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.12.png]]
	* `switchport trunk native vlan 10`
		* this is used to specify the native VLAN **and traffic in the native VLAN is sent untagged over the trunk**

2. ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.13.png]]
	* `switchport trunk allowed vlan all`
		* by default all VLANs are allowed on a trunk port, so allowing all VLANs will effectively return the interface to a default state

3. ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.14.png]]
	* `switchport trunk encapsulation dot1q`

4. ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.15.png]]
	* VID

5. ![[./_resources/Day_17_-_VLANs_(Part_2).resources/image.16.png]]
	* VLAN10  doesn't exist on the switch
