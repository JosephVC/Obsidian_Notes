
• What is the definition of TCP and UDP?  
• How are TCP and UDP different as communication protocols?  
• What are the standard communications protocols?  
• What are the default port numbers configured for each protocol?

- all this shit is at the ***Transport Layer***


- Port numbers are between 0 and 65535

![[Pasted image 20251208185433.png]]


- at the transport layer, IP sends data in the form of packets.. these can be damaged or otherwise fail at any time. 
	- this is why we need TCP, to ensure a reliable delivery of packets when needed
	- a ***connection oriented protocol*** prioritizes such stability and provides for the following
		- establishes a connection between the sender and recipient  using what is called a three-way handshake: SYN-ACK/ACK-ACK
		- assigns each packet a sequence number
		- allows an acknowledgement - ACK - that a packet has been received
		- allows a negative acknowledgement - NACK - and force a retransmission if there is missing or damaged packet
		- the transmission is terminated with a FIN handshake
	- all the above require multiple header fields, which can add over 20bytes to each packet
		- ***what the fuck is a header?***
			- think of the TCP/IP header as the lid on a bin, where the bin stores the data and the lid is covered in notations needed to get the bin where/where/how it should go
			- ![[Pasted image 20251214103605.png]]
				- source port - identifies the application or process that initiated the data transfer
				- destination port - identifies the application or process that is expecting the data
				- sequence number - like a tracking number for each packet making sure they arrive in the right order
				- ACK number - confirmation the packet was received
				- data offset - indicates the size of the overall header - how big the lid is - this helps with processing the overall packet
				- reserved - used for future use
				- control flag - these are switches that allow specific TCP functionality (making or ending a connection, managing the urgency of the data), adjusting window sizes
				- window size - the window for how much data a receiver can handle at once - this helps prevent network overload
				- checksum - value used for error detection
				- urgent pointer - notes the end of urgent data in order to prioritize its delivery
				- options - timestamps, segment size, or other optional information
	- ***following applications need to use TCP***
		- HTTPS
		- SSH

- ***User Datagram Protocol - UDP***
	- connectionless protocol 
	- no guarantee a packet will get to its destination, or do so in the right order or without corruption/damage
	- for urgent/time sensitive data such as streaming video or calls
		- missing data is seen as a glitch or stutter rather than breaking the whole transmission
	- ***Dynamic Host Configuration Protocol (DHCP)*** - used to request IP configuration information from a server
		- uses broadcast transmissions, which are not supported by TCP
		- if a response packet is not received, DHCP just keeps trying until it times out
	- ***Trivial file transfer protocol (TFTP)*** - uses its own ACK messaging, and does not use TCP

- ***Well-Known Ports***
- ![[Pasted image 20251214112835.png]]
- 