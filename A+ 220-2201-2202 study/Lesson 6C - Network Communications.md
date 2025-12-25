
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
		- 