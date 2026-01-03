
• What is the definition of TCP and UDP?  
• How are TCP and UDP different as communication protocols?  
• What are the standard communications protocols?  
• What are the default port numbers configured for each protocol?

- all this shit is at the ***Transport Layer***


- Port numbers are between 0 and 65535

![[Pasted image 20260103143907.png]]



- at the transport layer, IP sends data in the form of packets.. these can be damaged or otherwise fail at any time. 
	- this is why we need TCP, to ensure a reliable delivery of packets when needed
	- a ***connection oriented protocol*** prioritizes such stability and provides for the following
		- establishes a connection between the sender and recipient  using what is called a three-way handshake: SYN-ACK/ACK-ACK
		- assigns each packet a sequence number for the sake of tracking
		- sends an acknowledgement (ACK) that a packet has been received
		- if a packet is missing or damaged, a negative acknowledgement (NACK) is sent
		- the transmission is concluded with a FIN handshake
		- all the above at least 20 bytes to each packet
- Protocols using TCP are HTTPS and SSH


- User Datagram Protocol (UDP)
	- ***connectionless*** and non guaranteed way to send packets
	- protocols using UDP are DHCP and TFTP
		- DHCP uses broadcast transmissions, which are not supported by TCP
		- Trivial File Transfer Protocol (TFTP) does not use TCP as it has its own acknowledgement messaging

***Well Know Ports***

![[Pasted image 20260103145053.png]]
