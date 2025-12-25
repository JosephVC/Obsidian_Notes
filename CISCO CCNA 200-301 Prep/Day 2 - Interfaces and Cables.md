---
---
**Ethernet**

* collection of network protocols/standards
* network protocols exist to provide a common language/communication medium between a variety of different systems
	RJ-45 port 
	* RJ = Registered Jack
	* standard ethernet port
	* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/image.png]]
		* **Cat:** category of cable; in general the higher numbers represent faster speeds and higher frequencies (measured in Mhz)
* differences in an electrical signal are interpreted by a computer as either a 0 or a 1
	*  a single 0 or 1 is a **bit**
	* a collection of 8 bits is a **byte**
	* network speed is measured in **bits per second (Kpbs, Mbps, Gbps)**
* **Ethernet standards**
	* defined in **IEEE 802.3** standard
	* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.png]]
		* the **BASE** in 1xBASE-T stands for **baseband signaling**
		* **T** stands for **twisted pair**
	* the cables most often used in ethernet cables are **UTP (Unshielded Twisted Pair) cables**
		* unshielded means the cables have no metallic shield around them, which could make them more vulnerable to electrical interference 
		* twisted pair refers to how there are several pairs of wire twisted around each other - usually 8 individual wires in total
			* twisting helps protect against **EMI (Electromagnetic Interference)**
		* most ethernet cables are **straight-through cables**
			* the cable has two ends, and pin 1 on one end corresponds to pin 2 on the other end
		* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.2.png]]
	* **10/100BASE-T**
		* when a client computer is connected to a switch, it uses pins 1 and 2 to transmit data, and pins 3 and 6 to receive data
			* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.1.png]]
			* the above allows for **full duplex transmission (both devices can send and receive data at the same time, and no collisions of data can happen as different wires are used for sending and receiving)**
		* if a router is connected to a switch, the **same pins are  used to send and transmit data in full duplex**
		* if one type of device is connected to a second, **similar** device **the above connection won't work**
			* the transmitting pins on one side are connecting to the receiving pins on the other side
			* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.8.png]]
			* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.5.png]]
	* **Auto MDI-X**
		* per the above, two similar devices could not connect straight through but would need to cross over
		* **Auto MDI-X allows devices to automatically detect which pins are being used to transmit and receive data and adjust accordingly**
		* concerns about straight-through and crossover cabling is mainly for older equipment 
	* **1000/10GBASE-T**
		* each pair of wires are **bi-directional, meaning the wire pairs are not dedicated to either sending or receiving data**

**Fiber Optic Connections**

![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.4.png]]

* SFP Tranceiver accepts fiber optic cable
	* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.12.png]]
	* one connector is need to send data while the other cable is used to receive data
		* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.7.png]]
	* there are 4 main parts to a fiber optic cable:
		* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.3.png]]
	* main types of fiber optic cable
		* **single-mode**
			* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.10.png]]
			* **core is narrower (fiber is thinner)**
			* light enters at a single angle (mode) from a laser transmitter
			* allows a longer cable than both UTP and multi-mode fiber
			* more expensive due to laser-based SFP transmitter
		* **multi-mode**
			* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.6.png]]
			* core diameter is **wider** than single-mode
			* **allows multiple angles (modes)** of light waves to enter the fiberglass core
			* **allows longer cables than UTP, but shorter than single-mode fiber**
			* **cheaper** than single mode, as they use cheaper LED-based SFP transmitters
		* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.9.png]]
	* ![[./_resources/Day_2_-_Interfaces_and_Cables.resources/unknown_filename.11.png]]

**QUIZ**

1.  two old routers are connected via UTP cable, but data is not accurately sent and received between them.  what is the problem?

            - **they are connected with a straight-through cable, which can't be used with older equipment of the same type**
                    - a crossover cable - or using modern devices with MDI-X - would solve the problem
                    - because both routers transmit data on pins 1 and 2 a crossover cable is necessary to properly connect the transmit pins on 
                        one side of the connection to the receive pins (3 and 6) on the other side; Auto MDI-X allows devices to automatically 
                        detect which pins and wires another devices is using to transmit and receive data and adjust their operations accordingly

2. the company wants to connect switches in two separate buildings that are about 150 meters apart.  to keep costs down, what kind of cable should they use?

            - UTP is too short, so the next best option would be 1000BASE-T **multimode fiber** 

3. offices 3km apart are to be connected with what fiber?  at least **10GBASE-T** **single mode fiber, which supports distances of up to 10km**
4. a switch has Auto MDI-X supported, so what would happen if you connected to a similar switch with a straight-through cable?

        - the switches would operate normally, as Auto MDI-X would use the appropriate pins automatically

5. a switch needs to be connected to multiple computers on the same floor.  What kinds of cables would be needed?

        - UTP cable would be fine for this, provided the floor was not too large
