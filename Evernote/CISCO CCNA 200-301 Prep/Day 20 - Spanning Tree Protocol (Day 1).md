---
---
**Network Redundancy**

* redundancy is an essential part of network design
* modern networks are expected to run 24/7/365; downtime costs money
* if one network component fails, you must ensure the other components will take over with little or no downtime
* as much as possible, there must be redundancy at every possible point in the network

**Poorly Designed Network**

* **any one failure in the below network will lead to a cascade of failures in the network**
* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.png]]
* **Redundancy**
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.1.png]]
		* most PCs have a single network interface card (NIC), so they can only be plugged into a single switch.  However, important servers typically have multiple NICs allowing them to be plugged into multiple switches for redundancy.

**Broadcast Storms**

* a switch receiving a broadcast frame will flood the frame out of its interfaces (except the interface the frame was received on) ;
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.2.png]]
	* the switches involved will broadcast and rebroadcast the frames forever
	* while some frames will die per their Time to Live number, **the Ethernet header doesn't have a TTL field.  These broadcast frames will loop around indefinitely.  the network can become too congested to use**
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.3.png]]
	* each time a frame arrives on the switchport, the MAC address tables on each switch is updated; the constant updating of this MAC address table is known as **MAC address flapping**
		

**Spanning Tree Protocol (STP)**

* **layer 2 protocol**
* Classic Spanning Tree protocol is IEEE 802.1D
* Switches from ALL vendors run STP by default
* STP prevents L2 loops by placing redundant ports in a **blocking state**, essentially disabling the interface
	* these interfaces act as backups that can enter a **forwarding state** if an active (i.e. currently forwarding) interface fails
	* interfaces in a forwarding state behave normally; they send and receive all normal traffic
* interfaces in a blocking state only send or receive STP messages (called **Bridge Protocol Data Units or BPDUs)**
	* Bridges were used after hub technology but before switches; nowadays the term 'bridge' means 'switch'
* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.4.png]]
	* the red dot indicates a blocking state on of SW3's interfaces
	* for now, the direct connection between SW2 and SW3 does not exist
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.5.png]]
	* this means that if the connection between SW1 and SW2 were cut, the network would automatically compensate
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.6.png]]

* by selecting which ports are forwarding and which ports are blocking, STP creates a single path to/from each point in the network; this prevents L2 loops
* there is a set process that STP uses to determine which ports should be forwarding and which should be blocking
* STP-enabled switches send/receive **Hello BPDUs** out of all interfaces, the default timer is 2 seconds (the switch will send a **Hello BPDU** out of every interface, once every 2 seconds)
* if a switch receives a Hello BPDU on an interface, it knows that interface is connected to another switch (routers, PCs, etc. do not use STP, so they do not send Hello BPDUs)

* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.7.png]]
	* BPDUs are sent out of every switch interface
	* these BPDU's are used to advertise to other switches and to learn about other switches
* Switches use one field in the STP BPDU, the **Bridge ID** field, to elect a **root bridge** for the network
* The switch with the **lowest** Bridge ID becomes the root bridge
* **ALL** ports on the root bridge are put in a forwarding state, and other switches in the topology must have a path to reach the root bridge
* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.8.png]]
* the **Bridge Priority has been updated**
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.9.png]]
		* by adding the VID into the Bridge Priority, the switch will have a different bridge ID within each VLAN
* the **Bridge Priority Field**
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.10.png]]
		
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.12.png]]
		
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.11.png]]

* All interfaces on the root bridge are **designated ports**.  Designated ports are in a forwarding state

* if a switch is powered on, it assumes it is the root bridge
	* it will only give up its position if it receives a 'superior' BPDU (lower bridge ID)
* once the topology has converged and all switches agree on the root bridge, only the root bridge sends BPDUs
* other switches in the network will forward these BPDUs, but will not generate their own original BPDUs

* 2) Each remaining switch will select ONE of its interfaces to be its **root port**.  The interface with the lowest **root cost** will be the root port.  Root ports are also in a forwarding state.
	* **root cost**
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.13.png]]
	* the **root cost** is the total cost of the outgoing interfaces along the path to the root bridge
	* the ports connected to another switch's root port MUST be designated.  Because the root port is the switch's path to the root bridge, another switch must not block it
	* the root bridge has a cost of 0 across all interfaces
	* you don't count the cost of a receiving interface, just the sending interface
	* 1.  we now have SW1 as the root bridge
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.17.png]]
		
	* 2\. Now SW2 and SW3 will considers the root cost of its gigabit ethernet ports, which in both cases is 4
		* because the overall cost of G0/1 is 4 - the cost from SW1 is 0, but sending back from SW2 would be 4 - and the cost of sending/receiving on G0/0 adds up to 8, the **root port on SW2** is G0/1
		* because the overall cost of sending/receiving on G0/1 is 4 (cost is 0 sending from SW1) and the cost of sending/receiving on G0/1 is 8, **root port of SW3 is G0/0**

* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.14.png]]

![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.18.png]]

![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.19.png]]

* the **root bridge** will be SW2 ,as it has the lowest ID, therefore SW2 ports are all designated
* the **root ports** will be
	* G0/1 on SW4 - there is a cost of 4 on send/receive from SW2
	* G0/0 on SW1 - there is a cost of 4 on send/receive from SW2
	* G0/0 on SW3 - there is a tie between the cost of G0/0 and G0/1 on SW3, so we look at the lowest network ID of SW3's neighbors of SW4 and SW1; SW1 has the lower ID (based on MAC address)
		* SW1 is the  neighbor with the lowest network ID, so the G0/0 interface is the root port on SW3
	

there is another tie breaker that may be used to for figuring  out the root port

* the command `show spanning tree` provides the following output
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.15.png]]
	* note the `Prio.Nbr` field, which lists the **Spanning Tree Port ID**
		* STP Port ID = port priority (default 128) + port number
		* the **lower port number** itself is used as a tie-breaker if other factors are all tied
	* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.20.png]]
		* in the above, SW3 will select G0/2 as it connects to the **lowest port number on its neighbor SW1**
		* **the neighbor switch's port ID is used to break the tie, not the local switch's port ID**

* every collision domain has a single STP designated port
	* each link is a separate collision domain - in purple below
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.21.png]]
		* **how do we determine which port will be designated in a \*forwarding\* state?**
		* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.22.png]]
			

* ![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.16.png]]

**QUIZ**

![[./_resources/Day_20_-_Spanning_Tree_Protocol_(Day_1).resources/image.23.png]]

* the **root bridge** is SW3, because given that all the switch IDs are the same, we need to use the lowest MAC address, which belongs to SW3
	* all its ports are designated forwarding ports
* because all the ports are Gb ethernet, they have a root cost of 4
* the **root ports:**
	* G0/1 on SW1 - it has a lower cost
	* G0/0 on SW4, as it has a lower cost
	* G0/2 on SW2, as its neighbor's receiving port number is low
* the **designated ports:**
	* G0/2 on SW1, as it's neighbor's receiving port number is lower
	* G0/0 on SW3, as its connected to the G0/1 root port on SW1
		* G0/1 on SW3, as its connected to the G0/0 root port on SW4
	* G0/0 on SW1 as its connected to the G0/2 root port on SW2
* the **non designated ports :**
	* **G0/1 and G0/0 on** SW2
