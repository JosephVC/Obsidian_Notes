---
---
**ICMP** is an **network layer protocol** used by network devices to diagnose network communication issues, mainly to see whether data is reaching its intended destination in a timely manner.  The protocol is crucial for error reporting and detecting.  ICMP is commonly used on devices like routers.  ICMP can also be used **in a DDOS attack.**

when two devices are connected on a network, ICMP sends error to the sending device in case data was not received at the intended destination.  As an example, if a packet of data is too large for a router, the device will drop the packet and send an ICMP message back to the sender.  Unlike the **IP** protocol, ICMP is not on the **transport layer** and is thus a **connectionless protocol**.  a device does not need to open a connection with another device before sending an ICMP message.  Normal IP traffic will be sent with TCP, so two devices will attempt to set up a **TCP handshake** to ensure both devices are ready to receive data.  ICMP does not establish any sort of handshake nor does it allow targeting a specific port on a device.

Another use of ICMP is **network diagnostics.** both **traceroute** and **ping** operate using ICMP; **traceroute** is meant to display the literal physical route of devices a request passes through to reach its destination.  as the request moves between each device, it does a 'hop' and traceroute records the time between hops (this can help if there are any network delays).  **ping** is a simpler version of this, in that it tests the speed of a request between two devices, but does not provide information about routing or hops.  the ICMP **echo-request** and **echo-reply** messages are commonly used to ping

The above process can be exploited by attackers via an **ICMP flood attack** or **ping of death** attack.

* **ICMP flood**
	* this is where an attacker tries to overwhelm a target with ICMP echo-request packets.  The works because the target has to expend resources processing each request and responding to them
		* ![[./_resources/ICMP_(Internet_Control_Message_Protocol).resources/unknown_filename.1.png]]
	* **Ping of death**
		* an attacker sends a ping which is larger than the target machine's max allowable packet size, causing the target machine to crash
		* the packet gets fragmented on its way to the target, which then tries to reassemble to its original (excessive) size and the reassembled packet causes a buffer overflow
		* modern machines may be less susceptible than older machines
* **Smurf attack**
	* an attacker sends an ICMP packet from a **spoofed** source IP address
		* spoofing an IP address involves creating false source 
	* networking equipment replies to the packet, sending replies to the spoofed IP address and then flooding the target with unwanted ICMP packets
	* legacy equipment is most susceptible to this  

**ICMP Reply**

![[./_resources/ICMP_(Internet_Control_Message_Protocol).resources/unknown_filename.png]]
