---
---
QoS is designed to determine priority of network traffic in order to mitigate delays and packet loss

**IP Phones/voice VLANs**

* traditional phones operate over the **public switched telephone network (PSTN)**
	* this can also be called **Plain Old Telephone Service (POTS)**
* IP phones use **Voice Over IP (VoIP)** technologies to enable phone calls over a network such as the internet
* IP phones are connected to a switch as if it were any other end host
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.png]]

* IP phones have an internal, 3-port switch
	* one port is an **uplink** connecting to an external switch
	* another switch is a **downlink** to a PC
	* another switch connects internally to the phone itself
	* this configuration allows the IP phone to occupy a single switch port, where traffic from the PC passes through the phone to the larger network switch
		* ultimately this means we have to buy fewer network switches
		* it's recommended to **separate voice traffic from data traffic by putting them in different VLANs**, such as the **voice VLAN**
			* traffic from the PC will be untagged, but traffic from the phone will be tagged with a VLAN ID
		* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.1.png]]

* Another name for an **access port** is an **untagged port**
* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.2.png]]

* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.3.png]]
	* the highlighed output always shows up using the above command even if you are not on a trunk
* we ultimatley only use 3 switch ports instead of 6
* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.4.png]]
* now, we separate the IP and data VLANs
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.5.png]]

**Power over Ethernet (PoE)**

* PoE allows **Power Sourcing Equipment (PSE)** to provide power to **Powered Devices (PD)** over an ethernet cable
* Typically the PSE is a switch and the PDs are IP phones, IP cameras, wireless access points, etc.
* the PSE receives AC power from the outlet, converts it to DC power, and supplies that DC power to the PDs
* too much electrical current can harm devices, so there needs to be a way to regulate how much power a device receives
	* when a device is connected to a PoE enabled port, the PSE ( a switch) sends low power signals, monitors the response, and then determines how much power the PD needs
	* if the connected devices needs power the PSE supplies the power to allow the PD to boot
	* the PSE continues to monitor the PD and supply the required amount of power
* **power policing** can be configured to prevent a PD from taking too much power
	* **power inline police** configures power policing with the default settings: disable the port and send a Syslog message if a PD draws too much power
		* equivalent to **power inline police action err-disable**
		* the interface will be put in an 'error disabled' state and can be re-enabled with **shutdown** followed by **no shutdown**
	* **power inline police action log** does not shut down he interface if the PD draws too much power; it will restart the interface and send a Syslog message
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.6.png]]
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.7.png]]
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.8.png]]
		* the above table isn't necessary for the CCNA

**Quality of Service (QoS)**

* voice traffic and data traffic used to use entirely separate networks
	* **voice traffic** used the PSTN
	* **data traffic** used the IP network (WAN, internet, etc.)
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.9.png]]
		* PSTN is still in wide use
* QoS wasn't necessary as the different kinds of traffic didn't compete for bandwidth
* modern network typically **converge networks** in which IP phones, video traffic, regular data, etc. all share the same IP network
	* this enables costs savings along with more advanced features for voice and video traffic (collaboration software such as Teams, WebEx, etc.)
	* this means that different traffic needs to compete for bandwidth
	* QoS is a set of tools used by network devices to apply different treatment to different packets
* QoS is used to manage the following characteristics of network traffic
	1. **Bandwidth**
		* the overall capacity of the link, measured in bits/second (Kbps, Mbps, Gbps, ect.)
		* QoS tools allow you to reserve a certain amount of a link's bandwidth for specific kinds of traffic
			* ex: 20% voice traffic, 30% for specific kinds of data traffic, leaving 50% for all other traffic 

2. **Delay**
	* the amt. of time it takes traffic to go from source to destination = **one-way delay** 
	* the amt. of time it takes traffic to go from source to destination and return = **two-way delay**
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.10.png]]
3. **Jitter**
	* the variation in one-way delay between packets send by the same application
	* IP phones have a **jitter buffer** to provide a fixed delay to audio packets

      4.  **Loss**

* the % of packets sent that do not reach their destination
* can be caused by faulty cables
* can also be caused when a device's **packet queues** get full and the device starts discarding packets

* the following standards are recommended for **acceptable interactive audio** (ie phone call) quality:
	* **One-way delay:** 150ms or less
	* **Jitter:** 30ms or less
	* **Loss:** 1% or less
* if these standards are not met there could be a noticeable reduction in the quality of the phone call

**QoS - Queuing**

* if a network device receives messages faster than it can forward them out the appropriate interface, the messages are placed in a queue
* by default, queued messages will be forwarded in a First in First Out (FIFO) manner
	* messages will be sent in the order they are received
	* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.11.png]]
	* **what happens when the queue gets full?**
		* if the queue gets full new packets will be dropped; this is called **tail drop**
		* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.12.png]]
		* tail drop is harmful because it can lead to **TCP global synchronization**
			* to understand TCP global synchronization, we need to review **TCP sliding window**
				* hosts using TCP use the **sliding window** increase/decrease the rate at which they send traffic as needed
				* when a packet is dropped it will be re-transmitted
				* when a drop occurs, the sender will reduce the rate it sends traffic
				* it will then gradually increase again
			* when the queue fills up and tail drop occurs, all  TCP hosts sending traffic will slow down the rate at which they send traffic
				* these hosts will all then increase the rate at which they send traffic, which rapidly leads to more congestion, dropped packets, and the process repeats again
			* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.13.png]]
		* a solution to prevent tail drop and TCP global synchronization is **Random Early Detection (RED)**
		* when the amount of traffic in the queue reaches a certain threshold, the device will start randomly dropping packets from select TCP flows
		* those TCP flow that dropped packets will reduce the rate at which traffic is sent, but you will avoid global TCP synchronization in which **all** TCP flows reduce and then increase the rate of transmission at the same time in waves
		* in standard RED, all kinds of traffic are treated the same
		* an improved version **Weighted Random Early Detection (WRED)** allows you to control which packets are dropped depending on the traffic class
			* packets with lower priority will be dropped sooner

**QUIZ**

1. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.14.png]]

* a, d

2. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.15.png]]

* C

3. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.16.png]]

* b, c, e

4. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.17.png]]

* d

5. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.18.png]]

* A

6. ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.19.png]]

* D
* ![[./_resources/Day_46_-_Quality_of_Service_(QoS).resources/image.20.png]]
