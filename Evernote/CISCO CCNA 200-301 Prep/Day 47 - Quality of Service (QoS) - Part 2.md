---
---
**Classification**

* the purpose of QoS is to give certain kinds of network traffic priority over others during congestion
* **classification** organizes network traffic (packets) into traffic classes (categories)
* Classification is fundamental to QoS; you need to identify the types of traffic you want to give priority to
* there are many methods to classifying traffic
	* an ACL: traffic permitted by the ACL will be given priority while traffic denied will have less priority
	* **NBAR (Network Based Application Recognition)** - this performs a  **deep packet inspection** which goes beyond layer 3 and 4 and up to L7 to identify the specific kind of traffic
	* in L2 and L3 headers there are specific fields meant for this purpose
* the **PCP (Priority Code Point) -** field of the  802.1Q tag (in the Ethernet header) can be used to identify high/low priority traffic
	* this can **only** be used when there is a dot1q tag set; only when the VLAN tag is added to the ethernet header
* the **DSCP (Differentiated Service Code Point)** field of the IP header can also be used to identify high/low priority traffic

**PCP in QoS**

* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.png]]
	* to **mark** data is set the value in the PCP/DHCP fields, and then the traffic is prioritized

* because the PCP is found  in the dot1q header, it can only be used over one of the below connections
	* trunk links
		* this traffic is tagged with dot1q
	* access links with voice VLANs
* in the diagram below, trafic over R1 and R2, or between R2 and external destinations will not have a dot1q tag.  So, traffic over those links PCP cannot be marked with a PCP value
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.1.png]]
	* the connection between the phones and the switches are access ports with a voide
	* in this diagram, traffic between R1 and R2 or between R2 and external destinations will not have the dot1q tag; traffic over those links PCP cannot be marked with a PCP value

**IP TOS Byte**

* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.2.png]]
* the section highlighted in orange is the IPv4 header 
* these two fields make up the modern use of the TOS Byte
* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.3.png]]

**IP Precedence**

![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.4.png]]

* the standard IPP markings are similar to PCP
	* IPP 6 and 7 are reserved for 'network control' traffic (OSPF messages between routers)
	* IPP 5 = voice
	* IPP 4 = video
	* IPP 3 = voice signaling
	* IPP 0 = best effort
* with 6 and 7 reserved, 6 possible values remain
* although 6 values is sufficient for many networks, the QoS requirement of some network demand more flexibility

**DSCP**

* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.5.png]]
	* RFC 2474 ( from 1998) defines the DSCP field, and other 'DiffServ' RFCs elaborate on its use
	* with IPP updated to DSCP, new standard markings had to be made
		* the design and implementation of QoS is simplified by standard markings for different traffic
	* **standard markings**
		* **Default forwarding (DF) -** best effort traffic
		* **Expedited Forwarding (EF) -** low loss/latency/jitter traffic (mainly voice)
		* **Assured Forwarding (AF) -** a set of 12 standard values
		* **Class Selector (CS) -** a set of 8 standard values, provides backward compatibility with IPP
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.6.png]]
		* in configuring QoS, class maps are used to determine which traffic you want to match
		* in the above figure, CS0 isn't shown because it's the same as the **default** value
	* **DF/EF (Default forwarding)**
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.7.png]]
			* DF is used for best-effort traffic
			* DSCP marking for DF is 0
	* **EF (Expedited Forwarding)**
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.8.png]]
			* EF is used for traffic that require low latency, loss, or jitter
			* DSCP marking for EF is 46
	* **AF (Assured Forwarding)**
		* AF defines four forwarding classes; all packets in a class have the same priority
		* within each class, there are three levels of **drop precedence**
			* **higher drop precedence =** more likely to drop packets during congestion
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.9.png]]
			* the "X" is decimal number of the class
			* the "Y" is the decimal number of the drop precedence
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.10.png]]
			* there are 3 bits for the class and 2 for the drop precedence
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.11.png]]
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.12.png]]
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.13.png]]
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.14.png]]
		* **Formula to convert from AF values to decimal DSCP value = 8X + 2Y**
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.15.png]]

* **CS (Class Selector)** defines eight DSCP values for backward compatibility with IPP
	* the three bits that were added to DSCP are set to 0, and the original IPP bits are used to make 8 values
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.16.png]]

**RFC 4954**

* RFC 4954 was developed with the help of Cisco to bring all the above values together and standardize their use
* the RFC offers many specific recommendations, but here are some key ones
	* voice traffic = EF
	* interactive video = AF4x
	* streaming video = AF3x
	* high priority data = AF2x
	* best effort: DF

**Trust Boundaries**

* the trust boundary of a network defines where the devices on the network trust the QoS markings of received messages
* if markings are trusted, the device will forward the message without changing the markings
* if markings are not trusted, a device will change the markings according to whatever policy has been configured
* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.17.png]]
* if an IP phone is connected to a switchport, it is recommended to move the trust boundary to the IP phones
	* this is done via configuration on the switch port connected to the IPO phone
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.18.png]]
	* if a user marks their PCs traffic with a high priority, the marking will be changed (not trusted)
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.19.png]]

**Queuing/Congestion Mgmt**

* when a network device receives traffic at a faster rate than it can forward the traffic out the appropriate interface, packets are placed in that interface's queue as they wait to be forwarded
* if the queue becomes full packets that don't fit the queue are dropped **(tail drop)**
	* **RED/WRED** can avoid this by dropping packets early
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.20.png]]
* an essential part of QoS is the use of multiple queues
	* this is where classification plays a role; the device can match traffic based on various factors (like the DSCP marking in the IP header) and then place it in the appropriate queue
* a device is only able to forward one frame out of an interface at once, so a **scheduler** is used to decide which queue traffic is forwarded from next
	* **prioritization** allows the scheduler to give certain queues more priority than others
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.21.png]]

* a common scheduling method is **weighted round robin**
	* round robin = packets are taken from each queue in order, cyclically
	* weighted = more data is taken rom high priority queues each time the scheduler reaches that queue
* **CBWFQ (Class-Based Weighted Fair Queueing)**  is a popular method of scheduling, using a weighted round-robin scheduler while guaranteeing each queue a certain percentage of the interface's bandwidth during congestion
* **Round-robin scheduling is not ideal for voice or video traffic**
	* even if the voice/video traffic receives a guaranteed minimum amount of bandwidth, round-robin can add delay and jitter because even the high priority queues have to wait their turn in the scheduler
	* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.22.png]]
* **LLQ (Low Latency Queuing)** designates one (or more) queues as **strict priority queues**
	* this means that if there is traffic in the queue, the scheduler will **always** take the next packet from that queue until it is empty
	* this is very effective for reducing the delay and jitter of voice/video traffic
	* in the below example, the scheduler will prioritize the orange queue until it is empty
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.23.png]]
		* the downside is that **other queues can be starved if the priority queue always gets full of traffic**
		* **policing** can control the amount of traffic moving through queues

**Shaping and Policing**

* **traffic shaping/policing** are both used to control the rate of traffic
	* **shaping** buffers traffic in a queue in the rate goes over a configured rate
	* **policing** drops traffic if the traffic rate goes over the configured rate
		* policing has the option of re-making the traffic instead of dropping it
		* **burst traffic** over the configured rate is allowed for a short period of time
			* this accommodates data applications which typically have high bursts of data rather than constant streams
			* the amount of burst traffic is configurable
	* for both cases, classification can be used to allow for different rates for different kinds of traffic
	* why bother limiting the rate traffic is sent/received?
		* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.24.png]]

**QUIZ**

**1.**
![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.25.png]]

* b, d, e

**2.**
![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.26.png]]

* d

3. ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.27.png]]

* b

4. ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.28.png]]
	* a

5. ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.29.png]]

* b

![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.30.png]]

* D
* ![[./_resources/Day_47_-_Quality_of_Service_(QoS)_-_Part_2.resources/image.31.png]]
