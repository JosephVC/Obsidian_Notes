---
---
**Loopback Interfaces**

* a loopback interface is a virtual interface for the router
* it is always up unless it gets manually shut down
* it is not dependent on the physical interface
* provides a consistent IP address that can be used to identify and reach the router

**OSPF Network Types**

* the network type refers to the type of connection between OSPF neighbors (ethernet, etc.)
* three main OSPF network types
	* **broadcast network types**
		* enabled by default on Ethernet and FDDI (Fiber Distributed Data Interfaces)
			* FDDI is an old technology
			
	* **point-to-point**
		* enabled by default on PPP (Point-to-Point Protocol) HDLC (High-level Data Link Control) interfaces
	* **non-broadcast**
		* enabled by default on Frame Relay and X.25 interfaces

**Broadcast Network Type**

* routers **dynamically discover** neighbors by sending/receiving OSPF **Hello** messages using multicast address 224.0.0.5
* a **designated router (DR)** and **backup designated router (BDR)** must be elected on each subnet
	* if there are no OSPF neighbors, only a DR is elected)
* Routers that aren't the DR or BDR become DROther
* **Each subnet needs a DR**
* **The BR/BDR election order of priority**
	1. highest OSPF interface priority
	2. highest OSPF Router ID
* first place gets to be the DR of the subnet, second place is the BDR
	* when the DR goes down, the BDR becomes the new DR, then an election is held for the next BDR
		
* the default OSPF interface priority is 1 on all interfaces
* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.png]]
* the DR/BDR election is 'non-preemtive.  Once the DR/BDR are selected they will keep their role until OSPF is reset, the  interface fails/is shut down, etc.
* `clear ip ospf process`  is the command to clear the OSPF process on a router
* in the broadcast network type,routers will only form a full OSPF adjacency with the DR and BDR of the segment
* therefore, routers only exchange LSAs with the DR and BDR.  DROthers will not exchange LSAs with each others
* all routers will still have the same LSDB, but this reduces the amount of LSAs flooding the network
* messages to the DR/BDR are multicast using address 224.0.0.6
* the DR and BDR will form a FULL adjancency with ALL routers in the subnet; DROthers will form a full adjacency only with the DR/BDR

**OSPF Point-to-Point Network Type**

* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.1.png]]

* enabled on **serial** interfaces using the **PPP** or **HDLC** encapsulations by default
* routers **dynamically discover** neighbors by sending/listening for OSPF Hello messages using multicast address 224.0.0.5
* **a DR and BDR are not elected**
* these encapsulations are used for 'point-to-point' connections
* therefore there is no point in electing DR and BDR
* the two routers will form a Full adjacency with each other

* **Serial Interfaces**
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.2.png]]

*  ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.3.png]]

* **Ethernet** interfaces use the speed command to configure the interface's operating speed; **serial interfaces** use the **clock rate** command 

* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.5.png]]

**Configure the OSPF Network Type**

* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/unknown_filename.4.png]]

* You can configure the OSPF network type on an interface with `ip ospf network [network type]`
* for example if two routers are directly connected wit an Ethernet link, there is no need for a DR/BDR; you can configure the point-to-point network type in this case
* NOTE: not all network types work on all link types (ex: a serial link cannot use the broadcast network type as the serial link does not support L2 broadcast frames, which the broadcast type requires)
* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.png]]

**OSPF Neighbor Requirements**

1. Area numbers must match
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.1.png]]

2. Interfaces must be within the same subnet
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.2.png]]

3. OSPF process must not be `shutdown`
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.3.png]]

4. OSPF Router IDs must be unique
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.4.png]]

5. Hello and Dead timers must match
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.5.png]]

6. authentication settings must match
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.6.png]]

7. IP MTU settings must match
	* if if settings don't match, they can become OSPF neighbors, but OSPF doesn't operate properly
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.7.png]]

   8. OSPF Network Type must match

* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.8.png]]
* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.9.png]]

**OSPF LSA Types**

* the OSPF LSDB is made up of LSAs
* There are 11 types of LSA, but there are only 3 you should be aware of for the CCNA:
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.10.png]]

**QUIZ**

![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.11.png]]

* B

![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.12.png]]

* c
	* d is incorrect as it won't form an adjancency to itself

![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.13.png]]

* A and D
	* ![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.14.png]]

![[./_resources/Day_28_-_OSPF_(Part_3).resources/image.15.png]]

* type 2
