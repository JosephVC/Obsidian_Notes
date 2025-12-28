---
---
**Functions of Layer 4 (Transport Layer)**

* Provides transparent transfer of data between end hosts
	* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.png]]
* Provide (or not) various services to applications
	* reliable data transfer
	* error recovery
	* data sequencing
	* flow control
* Provides **Layer 4** addressing (**port** numbers) - **not the physical ports**
	* identify the Application Layer protocol
	* Provides session multiplexing
	* the following ranges have been assigned by **Internet Assigned Numbers Authority (IANA)**
		* **well-known** port numbers: 1-1023
		* **registered** ports: 1024 - 49151
		* **ephemeral/private/dynamic** ports: 49152 - 65535
	* port numbers are a function of both of the main functions of the L4 protocols : TCP and UDP

**Port Numbers/Session Multiplexing**

* a session is an exchange of data between two or more communicating devices

**Transmission Control Protocol (TCP)**

* TCP is connection-oriented
	* Before actually sending data to the destination host, the two hosts communicate to establish a connection.  Once a connection is established, the data exchange begins
* TCP provides reliable communication
	* the destination host must acknowledge that it received each TCP segment
	* if a segment isn't acknowledged, it is sent again
* TCP provides sequencing
	* Sequence numbers in the TCP header allow destination hosts to  put segments in the correct order even if they arrive out of order
* TCP provides flow control
	* the destination host can tell the source host to increase/decrease the rate that data is sent
* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.1.png]]
	* **Window size** is used for flow control

**TCP Establishing Connections: Three-Way Handshake**

1. the originating PC will send a TCP segment to a server with the **SYN** flag set (that particular bit is set to 1)
2. the server will respond TCP segment with the **SYN** and **ACK** flag bits set to 1
3. the PC will respond with a TCP segment with the **ACK** flag set

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.2.png]]

**TCP Terminating Connections - Four-way Handshake**

* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.3.png]]

**TCP: Sequencing/Acknowledgment**
![[./_resources/Day_30_-_TCP_&_UDP.resources/image.4.png]]

* sequence numbers allow the hosts to know the correct order of segments if they arrive out of order
* the sequence numbers going back and forth can get much larger than 1, and don't necessarily increase by 1 with each message

**TCP Retransmission**

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.5.png]]

**TCP Flow Control: Window Size**

* it is inefficient to acknowledge every single segment
* the **window size** field allows more data to be sent before an acknowledgement is required
	* the size of the window can be adjusted using the **sliding window**

**User Datagram Protocol (UDP)**

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.6.png]]

* not connection oriented, but is connectionless
	* the sending hos does not establish a connection with the destination host before sending data; the data is simply sent
* UDP **does not** provide reliable communication
	* when UPD is used, acknowledgments are not sent for received segments.  if a segment is lost, UDP  has no mechanism to re-transmit it.  Segments are sent as a 'best effort'
* UDP does not provide sequencing
	* There is no sequence number field in the UDP header .  If segments arrive out of order, UDP has no mechanism to put them back in order
* UDP has no flow control
	* it has no mechanism like TCP's window size

**Comparing TCP and UDP**

* TCP provides more features than UDP, but at the cost of additional **overhead**
* For applications that require reliable communication - downloading a file - TCP is preferred
* There are some applications that use UDP, but provide reliability within the application itself
* Some applications use both TCP and UDP based on the situation
* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.7.png]]
	* both provide L4 addresses and port numbers

**Port Numbers**

* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.13.png]]
* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.14.png]]
* ![[./_resources/Day_30_-_TCP_&_UDP.resources/image.15.png]]
	
* **TCP**
	* FTP - 20 & 21
	* SSH (Secure Shell)- used to connect to the CLI of routers and switches -  22
	* Telnet - also connects to CLI of devices - 23
	* SMTP (Simple Mail Transfer Protocol) - used for sending email - 25
	* HTTP (HyperText Transfer Protocol) - commonly used for accessing webpages - 80
	* POP3 (Post Office Protocol 3) - Port 110
	* HTTPS (HyperText Transfer Protocol Secure) - 443
	* IMAP - port 143
* **UDP**
	* **DHCP (Dynamic Host Configuration Protocol) - 67 (server), 68 (client)**
	* TFTP (Trival File Transfer Protocol) - 69
	* SNMP (Simple Network Management Protocol) - 161 (agent), 162 (manager)
	* Syslog - 514
		
* **TCP  & UDP**
	* **DNS (Domain Name System) - 53**
		* usually uses UDP, but can sometimes use TCP

QUIZ

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.8.png]]

* A

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.9.png]]

* C)
	* the destination port number depends on the application layer protocol but the source port number should be selected from the Ephemeral port range

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.10.png]]

* error recovery, flow control, sequencing

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.11.png]]

* SSH, SMTP, HTTPS

![[./_resources/Day_30_-_TCP_&_UDP.resources/image.12.png]]

* 28
	* TCP uses forward acknowledgement, so it acknowledges that it received a segment **by stating the next segment it expects to receive;** the ACK field will be at least one higher than the original segment
