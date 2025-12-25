---
---
**Spanning Tree Port States**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.png]]

* root/designated ports remain stable in a **forwarding** state
* non-designated ports remain stable in a **blocking** state
* **listening** and **learning** are transitional states which are passed through when an interface is activated, or when a **blocking** port must transition to a Forwarding state due to a change in the network topology
* a **Disabled state** refers to a component that is administratively disabled

**Blocking STP Port State**

* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.1.png]]
	* non-designated ports are in a **blocking state**
	* interfaces in a blocking state are effectively disabled to prevent loops
	* Interfaces in a blocking state to not send/receive regular network traffic
	* interfaces in a blocking state receive STP BPDUs
		* receiving these BPDUs is necessary to get an idea of the spanning tree topology and be ready to transition to a forwarding state
			
	* interfaces in a blocking state do NOT forward STP BPDUs
	* interfaces in a blocking state do NOT learn MAC addresses

**Listening STP Port State**
![[./_resources/Day_21_-_STP_(Part_2).resources/image.2.png]]

* after the blocking state, interfaces with the Designated or Root role enter the listening state
	* non designated ports are always blocking
* the listening state is 15 seconds long by default; this is determined by the **Forward delay** timer
* an interface in the Listening state ONLY forwards/receives STP BPDUs
* an interface in the Listening state does NOT sent/receive regular traffic
* an interface in the Listening state does NOT learn MAC addresses from regular traffic that arrives on the interface

**Learning STP Port State**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.3.png]]

* after the Listening state, a Designated or Root port will enter the **Learning state**
* the Learning state is 15 seconds long by default; this is determined by the **forward delay timer (**the same timer used for both the Listening and Learning states)
* an interface in the Learning state ONLY sends/receive STP BPDUs
* an interface in the learning state does NOT send/receive regular traffic
* an interface in the learning state **LEARNS** MAC addresses from regular traffic that arrives on the interface

**Forward STP Port State**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.4.png]]

* root and designated ports are in a **Forwarding state**
* a port in the Forwarding state operate as usual
* a port in the forwarding state sends/receives BPDUs
* a port in the forwarding state sends/receives normal traffic
* a port in the forwarding state learns MAC addresses 

![[./_resources/Day_21_-_STP_(Part_2).resources/image.5.png]]

**Spanning Tree Timers**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.6.png]]

* other switches in the network do not originate their own BPDUs, but will forward BPDUs they receive
* switches will only forward BPDUs on their **designated ports , but not their root ports or non-designated ports**

* Max Age timer
	* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.7.png]]
		* a forwarding interface **can** move directly  to a blocking state (there is no worry about creating a loop by blocking an interface)
		* a blocking interface **cannot** move directly to a forwarding state; it must go through the listening and learning states

**Spanning Tree BPDU**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.11.png]]

	
* **note the destination of the Cisco BPDU:** ![[./_resources/Day_21_-_STP_(Part_2).resources/image.8.png]]
* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.9.png]]
* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.10.png]]

**Spanning Tree Extras**
![[./_resources/Day_21_-_STP_(Part_2).resources/image.12.png]]

* the orange light means the switch is not forwarding yet but rather is going through the listening and learning states
	* it will take approx. 30 seconds for the light to turn green, meaning the switch is forwarding
* **Portfast** allows a port to move immediately to the **forwarding** state, bypassing **listening** and **learning**
	* if used, it must be enabled **only on ports connected to end hosts**
	* if enabled on a port connected to another switch it could cause a L2 loop
	* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.13.png]]
* **BPDU Guard**
	* if an interface with BPDU guard enabled receives a BPDU from another switch, the interface will be shut down to prevent a loop from forming
	* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.14.png]]
	* when a BPDU arrives on a BPDU Guard-enabled port:
		* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.15.png]]
		* to enable the port again:
			* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.16.png]]
			* if you are still connected to a switch the interface will immediately be disabled again:
				* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.17.png]]
					

* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.18.png]]
	
* **Make sure to learn PortFast and BPDU Guard**

**Configure the Spanning Tree mode**

* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.19.png]]

**Configure the Primary Root Bridge**

* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.20.png]]
	* if you then check the running config, you see the following command is actually applied
		* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.21.png]]

**Configure the Secondary Root Bridge**

![[./_resources/Day_21_-_STP_(Part_2).resources/image.22.png]]

* this is the actual command that is applied:
	* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.23.png]]

**STP Load Balancing**

* if you have multiple VLANs in your network, blocking the same interface in each VLAN is a waste of interface bandwidth; as that connection will be doing nothing just waiting for some connection to fail so it can start forwarding

![[./_resources/Day_21_-_STP_(Part_2).resources/image.24.png]]

* SW1
	* spanning`-tree vlan 10 root primary`
	* `spanning-tree vlan 20 root secondary`
* SW2
	* `spanning-tree vlan 20 root primary`
	* `spanning-tree vlan 10 root secondary`

**Configure STP Port Settings**

* ![[./_resources/Day_21_-_STP_(Part_2).resources/image.25.png]]

![[./_resources/Day_21_-_STP_(Part_2).resources/image.26.png]]

* enable PortFast on the switch port you connect the PC to
* reduce the STP forward delay time

![[./_resources/Day_21_-_STP_(Part_2).resources/image.27.png]]

* 128
	* the first half of the port ID, 0x80, is the STP port priority
		* this is equivalent to 128 in decimal

![[./_resources/Day_21_-_STP_(Part_2).resources/image.28.png]]

* BPDU guard
	* this will shut down an interface if an BPDU is received on the interface to prevent any potential loops

ExSim Max Question

* You want to decrease the amt. of time it takes for switch ports on switchA to being forwarding.  PortFast is not configured on any of the switch ports on SwitchA.  you use the command `spanning-tree portfast default` command from global configuration mode. . **which of the ports on SwitchA will use portfast**
	* **all access ports**
