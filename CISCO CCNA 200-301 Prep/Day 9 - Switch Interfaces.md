---
---
**Switch Interface**

* Routers will tend to have far fewer ports than switches do, as the switches will need to connect to a wide variety of end hosts while the routers will need to connect to only a few other networks, including the internet

**Interface Commands**

* the command **show ip interface brief** pulls up each interface, its IP address, whether it is OK, status, method, and protocol
* ![[./_resources/Day_9_-_Switch_Interfaces.resources/image.png]]
* the command show interface status
	* ![[./_resources/Day_9_-_Switch_Interfaces.resources/image.1.png]]
	* the **Port** lists each interface
	* the **Name** field is the descriptor of the interface
	* the **Status** field is whether the interface is connected or not
	* the **Vlan** field has a default of 1
	* the **Duplex** field indicates whether the device can send and receive data simultaneously
	* the **Speed** field has an auto indicator, which allows the interface to function at the highest speed it can; a-100 means the device can communicate at 100mbits/sec
	* the **Type** field is the physical connection type for the interface

**Full/Half Duplex**

* **half duplex** - the device cannot send and receive data at the same time.  If it is receiving a frame, it must wait before sending one
* **full duplex** - the device can simultaneously send+receive data without needing to wait
	* most modern devices are full duplex

**LAN Hubs**

* to better understand half-duplex understand the hub
* a hub is an older technology than the switch
	* the hub is simply a **repeater**
		* any frame it received it then floods with an unknown unicast frame
			* ![[./_resources/Day_9_-_Switch_Interfaces.resources/image.2.png]]
	* if two PCSs try sending frames at the same time the hub isn't advanced enough to try and broadcast one after the other but will broadcast both at the same time
		* sending these two frame simultaneously will cause a **collision** as they get repeated by the hub
			* this is why all devices connected to a hub are part of a **collision domain**, as any data they send over the hub can collide
				* ![[./_resources/Day_9_-_Switch_Interfaces.resources/image.3.png]]
					

**CSMA/CD**

* **Carrier Sense Multiple Access with Collision Detection**
* describes how devices avoid collision in a **half duplex** situation, and how the react when collision occur
* before sending frames, they listen to the collision domain until they detect that other devices are not sending
* if a collision does occur, the device sends a jamming signal to inform the other devices that a collision happened
* each device will wait a random period of time before sending frames again
* wash rinse repeat

**Collision domains**

* modern switches are more sophisticated than hubs
* hubs operate at L1, repeating whaterver they receive
* switches operate at L2, using Layer 2 addressing - MAC addressing - to send data to a device
* switches also won't try sending two frames to the same host at once
* switches increase the number of collision domains
	* ![[./_resources/Day_9_-_Switch_Interfaces.resources/image.4.png]]
	* as all these devices are separated out, they can operate in full duplex as they no longer have to worry about sending data directly to other devices

**Speed/Duplex Autonegotiation**

* interfaces that can run at different speeds (10/100 or 10/100/1000) have default settings of **speed auto** and **duplex auto** 
* interfaces 'advertise' their capabilities to the neighboring device, and they negotiate the best **speed** and **duplex** settings they are both capable of
* what if autonegotiaton  is disabled on the device connected to the switch
	* **speed** - the switch will try to sense the speed that the other device is operating at
		* if it fails to sense the speed, it will use the slowest supported speed (ie 10 Mbps on a 10/100/1000 interface)
	* **duplex** - if the speed is 10 or 100 Mbps, the switch will use half duplex
	* there is the potential for a **duplex mismatch** which will result in collisions and poor network performance

**Interface Errors**

* **runts** - frames that are less than the minim size for ethernet (64 bytes)
* **giants -** frames that are larger than the maximum frame size (1518 bytes)
* **CRC -** frames that fail the CRC check
* **Frame -** frames that have an incorrect format (due to some error)
* **Input errors -** total of various counters, such as the above four
* **output errors -** frames the switch tried to send, but failed to to an error
* **all the above errors are the same on a router**

**QUIZ**

1. There is a duplex mismatch between two switches; autonegotiation is disabled.  What is the result?
	* collisions will occur

2.  What is used on half-duplex interfaces to detect and avoid collisions

* CSMA/CD

3.  which command shows various counters of errors detected on an interface

* show interfaces

4. Which are examples of errors that might occur on a network interface?
	* runts, giants, CRC

5. two switches are trying to autonegotiate, but autonegotiation is disabled on switch2.  S2's interface is configured with a speed of 100 Mbps at full duplex.  What speed and duplex setting with S1 use, assuming it senses the speed of S2?
	* 100 Mbps/half duplex
