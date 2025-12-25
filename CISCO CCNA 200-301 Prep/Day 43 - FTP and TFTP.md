---
---
**FTP and TFTP**

* **FTP (File Transfer Protocol), TFTP (Trivial File Transfer Protocol)** are industry standard protocol for transferring files over a network
* both use a **client-server model**
	* both models allow a client to copy files to and from a server
* for network engineers, the most common usage of these protocols is to upgrade the OS of a network device
	* you can download a new OS using FTP/TFTP and then restart the device using the new IOS image
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.png]]

**TFTP**

* has more basic features than FTP
	* can only copy a file to and from a server
* was released after FTP but does not replace FTP; made to have something  just good enough to transfer files
* TFTP does not use encryption, so all data is sent plain text
* TFTP does not use authentication, so all severs will respond to TFTP requests
* the lack of security features means TFTP is best used in controlled circumstances to transfer small files
* **TFTP listen on UDP port 69**
* UDP is connectionless and doesn't provide reliability with retransmissions
	* has other built-in reliability features

**TFTP**

* Every TFTP data message is acknowledged
	* if the **client is transferring** **files** to a server, the **server** will send Ack messages
	* if the **server is transferring files** to a client, the **client** will send Ack messages
* there are timers set on when to receive messages, and if a messages isn't received in time the waiting device will resend the previous message
	* TFTP uses **lock step communication**, where the client and server alternatively send messages until the whole transmission is complete, with retransmissions sent as necessary
		* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.1.png]]

**TFTP Connections**

* There are three phases to TFTP file transfer
	* **Connection -** TFTP clients sends a request to the server, and the server responds back, initializing the connection
	* **Data Transfer -** the client and server exchange TFTP messages; one sends data and the other sends acknowledgements
	* **Connection Termination -** after the last data message has been sent, a final acknowledgement is sent to terminate the connection
	* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.2.png]]

**TFTP TID**

* when the client sends the first message to the server, the destination port is UDP port 69 and the source is a random ephemeral port
	* the random port is called the **Transfer Identifier (TID)** and identifies the data transfer
* the server then selects a random TID to use as the source port for when it replies, **not port 69**
* when the client sends the next message, the destination port will be the server's TID, **not port 69**
* the client and server continue using these random ports throughout the data transfer
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.3.png]]

**FTP - File Transfer Protocol**

* originally developed in 1971
* **FTP uses TCP port  20 and 21**
* usernames/passwords are used for authentication, but there is no authentication
* as an upgrade to FTP, FTPS (FTP over SSL/TLS) can be used
* SSH File Transfer Protocol (SFTP) can also be used for greater security
* FTP is more complex than TFTP and allows not only file transfers , but clients can also navigate file directories, add and remove directories, file lists,  etc.
	* TFTP can only give/take from a server, while FTP has a broader set of commands to use
* the client sends **FTP commands** to the server to perform a variety of functions

**FTP Control Connections**

* FTP uses two types of connections
	* an **FTP control** connection (**TCP 21)** is established  and used to send FTP commands and replies
	* when files or data are transferred separate **FTP data (TCP port 20)** connections are established and terminated as needed
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.4.png]]

**Active Mode FTP Data Connections**

* the **normal** mode of initiating FTP data connections
* the default method of establishing FTP data connections is **active mode** , in which the server initiates the TCP connection
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.5.png]]
	

**Passive Mode FTP Data Connections**

* in situations where the client is behind a firewall, the **client may need to initiate a data connection**.  the firewall could be blocking incoming connections from the server.  this calls for **FTP passive mode** as the firewall will not allow connections initiated from something external
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.6.png]]

**FTP v TFTP**
![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.7.png]]

**IOS File Systems**

* a file system is a way of controlling how data is stored and retrieved
* the `show file systems` command allows you to view the file systems of a Cisco IOS device
	* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.8.png]]

**Upgrading Cisco IOS**

* the `show version` command will show the current version of IOS on a device
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.9.png]]
	
* You can show the contents of flash with `show flash`
	
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.10.png]]
	

**Copying Files w/TFTP**

* `copy --source-- --destination--`
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.11.png]]

**Upgrading Cisco IOS**

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.12.png]]
* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.13.png]]

**Copying Files - FTP**

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.14.png]]

**Command Review**

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.15.png]]

**QUIZ**

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.16.png]]
	* B, D

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.17.png]]
	* A)
		* because the command requires a source and destination, you simply note the external TFTP server and then the local flash storage

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.18.png]]
	* C
		* both active and passive mode apply **only** to the FTP data connection because **the client always initiates the control connection;**
		* in active mode the server initiates the data connection, but in passive mode the client initiates the data connection

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.19.png]]
	* D

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.20.png]]
	* B, C

* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.21.png]]
	* C, D
	* ![[./_resources/Day_43_-_FTP_and_TFTP.resources/image.22.png]]
