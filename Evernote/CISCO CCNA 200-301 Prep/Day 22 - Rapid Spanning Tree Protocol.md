---
---
* regular STP can be slow, taking up to 50 seconds for networks to fully connect
	* rapid spanning tree makes this process faster

**Spanning Tree Versions**

![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.png]]

**Rapid STP**

* **Cisco's summary** - RSTP is not a timer-based ST algorithm like 802.1D, thus offering an improvement of 30 seconds or more that 802.1D takes to move a link to forwarding.  the heart of the protocol is a new bridge-bridge handshake mechanism which allows ports to move directly to forwarding
	* the traditional timers in STP were long to make sure no loops were created while forwarding

* Similarities between STP and RSTP
	* both serve the same purpose, to block certain ports to prevent L2 loops
	* both elect a root bridge using the same rules
	* both elect root ports using the same rules
	* both elect designated ports using the same rules
* Port costs were updated for RSTP
	* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.1.png]]

* RSTP Port States
	* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.2.png]]

* **RSTP Port Roles**
	* the **root port** role remains unchanged
		* the port that is closest to the root bridge becomes the root port for the switch
		* the root bridge is the only port that doesn't have a root port
	* the **designated port** role remains unchanged
		* the port on a segment (collision domain) that sends the best BPDU is that segment's designated port (only one per segment)
			* the other port is either a root port or undesignated ports
	* the **non-designated port** role is split into two roles under RSTP
		* the **alternate port** role
			* this is a discarding port that receives a superior BPDU from another switch
			* this  is like a blocking port in classic STP
			* the alternate port acts as a backup to the root port
				* if the root port fails, the switch can move its best alternate port to forwarding
				* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.3.png]]
					
		* the **backup port** role
			* discarding port that receives a superior BPDU from **another interface on the same switch**
			* this only happens when two interfaces are connected to the same collision domain (via a hub)
			* hubs are not used in modern networks, so you will probably not encounter an RSTP backup port
			* functions as a backup for a designated port
				* the interface with the lowest port ID will be selected as the designated port and the other will be the backup port

**RSTP: BackboneFast functionality**

* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.4.png]]
* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.5.png]]

![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.6.png]]

* the neighbor bridge ID for SW4 G0/1 has a lower ID than G0/0, so that's the designated port on SW4 - G0/0 is a backup port
* SW3's G0/0 port has a lower ID than G0/1, so it is designated - G0/1 is a backup port

![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.7.png]]

* all switches RSTP send their own BPDUs every hello time (2 seconds)
* switches 'age' the BPDUs information much more quickly.  in classic STP, a switch waits 10 hello intervals (20 seconds).  in RSTP, a switch considers its neighbor lost if it misses 3 BPDUs (6 seconds); it will then flush all MAC addresses learned on that interface
	* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.8.png]]

**RSTP Link Types**

* RSTP distinguishes between three different link types
	* **edge -** a port that is connected to an end host.  Moves directly to forwarding, without negotiation
		* because there is no risk for creating a loop, they can move straight to the forwarding state without the negotiation process
		* they function like classic STP port with PortFast enabled
		* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.9.png]]
		* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.10.png]]
			
	* **point-to-point -** a direct connection between two switches
		* function in full duplex
		* you don't need to configure the interface as being point-to-point as it should already be detected
		* below is the command to set up a point-to-point link type; the green 'P'

* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.11.png]]
	

* **shared -** a connection to a hub; must operate in half-duplex mode
	* the interface should be detected so there is no need to configure it explicitly
	* if there is a need to manually configure this link:
		* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.12.png]]
		* the below would be shared links in our network diagram
			* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.13.png]]

**QUIZ**

2. ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.14.png]]
	\- PortFast, UplinkFast, BackboneFast
	
3. ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.15.png]]
	* `spanning-tree portfast`

4. ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.16.png]]
	* root bridge = SW1
		* designated ports  = G0/1, G0/2, G0/0
		* edge ports = G0/0
			
	* SW2
		* receiving ports = G0/0
		* designated ports = G0/1, G0/3
			* SW2 has a lower root cost, so its ports are designated
		* backup ports = G0/2
		* edge ports = G0/3
	* SW3
		* r. ports = G0/2
		* d. ports = G0/0, G0/3
		* edge ports = G0/3
	* SW4
		* d. ports = G0/2
		* r. ports - G0/0
		* block. ports = G0/1
		* edge port = G0/2
	* every single, direct connection between the switches are **point-to-point links**
	* the connections between the switches and the hub are **shared links**
	* ![[./_resources/Day_22_-_Rapid_Spanning_Tree_Protocol.resources/image.17.png]]
		
5. which of the following option STP features reduces convergence time by immediately placing edge ports into a forwarding state?
	* **PortFast**
