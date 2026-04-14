
- What services are commonly found on modern networks?
- What port numbers are associated with the various services found on modern networks?
- How does a web server function?
- What are the services utilized by email systems and servers?
- How do remote access and monitoring services assist system administrators?


***File/Print Servers***
- one of the core functions of a network is to provide access to disk and print functions, which is implemented as a client/server architecture
	- the server is hosting the given disk or printer
	- a server disk allowing other clients to access it  a ***file share***, where the machines that access the file share are clients

***Server Message block*** (SMB)
- application protocol underpinning the file and print sharing on windows networks
	- usually runs on TCP port 445
- SMB3 is the current protocol
	- SMB1 is disabled by default due to security vulnerabilities 
		- SMB1 can also be referred to as Common Interent File System (CIFS)


- ***Network Basic Input/Output system
	- early Windows networking protocol did not use TCP/IP but rather NetBIOS
	- currently obsolete as the current protocols are TCP/UDP, IP, and DNS
	- NetBIOS should be disabled on machines as its outdated nature presents a security threat

- ***File transfer Protocol (FTP)
	- used to upload and download files over a network
	- uses TCP port 21 to establish a connection and TCP port 20 for transferring data
	- standard FTP is encrypted 
		- encrypted versions of FTP are ***FTP Secure (FTPS)*** and ***FTP over Secure Shell (SFTP)

- ***Database Servers***
	- database servers provide a way to store a shit ton of unstructured and structured data
	- basic spreadsheets are a flat file format
	- relational databases are the most common form of database
		- often use the Structured Query Language (SQL)
		- examples are Oracle, MySQL and MariaDB
	- non-relational databases are for very large amounts of data and are very flexible as to what they can store
		- examples include MongoDB, CouchDB, Amazon SimpleDB

- ***Web Servers***
	- allow client access over HTTP or HTTPS
	- servers can be over the whole Internet or a local network

- ***HyperText Transfer Protocol (HTTP)
	- enables clients (via web browsers) to request resources from an HTTP server
	- uses TCP port 80 
	- starts by initiating a GET request, and the server either returns the requested data or throws an error code
	- protocol is usually made to work with HTML web pages

- ***Uniform Resource Locator***
	- a URL contains all the information needed to access an item on the Internet
		- The protocol describes the access method or service type being used.
		 •  The host location is usually represented by a FQDN. The FQDN is not case-sensitive. The host location can also be an IP address; an IPv6 address must be enclosed in square brackets.
		 •  The file path specifies the directory and file name location of the resource (if required). The file path may or may not be case-sensitive, depending on how the server is configured.
	- ![[Pasted image 20260118132501.png]]
	- Hypertext Transfer Protocol Secure (HTTPS)
		- version of HTTP encrypted with SSL
		- uses TCP port 443 by default
		- to implement HTTPS, a server has digital certificates installed by a certificate authority (CA)
			- these certificates uses encrypted data to prove the identity of a server to the client, assuming the client trusts the given CA
			- uses public/private encryption key pair
				- private key is kept on the server while the public key is given to the clients via the digital certificate 
			- the client and server use the key pair in the certificate to set up an encrypted tunnel - to decrypt this tunnel you need both the public key and private key

- ***Mail servers***
	- ![[Pasted image 20260118133616.png]]
	- ***Simple Mail Transfer Protocol (SMTP)
		- specifies how mail is delivered from one mail domain to another
		- the senders SMTP server discovers the IP address of the recipient's SMTP server using the domain portion of the recipient's email address - the part after the @ symbol
		- Port TCP 25 - is used for message relay between SMTP servers - these transmissions are usually insecure
			- mail servers are also called ***Message Transfer Agents (MTA)
		- Port TCP 587 - are for mail clients - ***Message Submission agents (MSAs)*** - to submit messages for delivery by an SMTP server 
			- encryption should be set up for this

- ***Mailbox Servers***
	- SMTP is used to deliver mail to server hosts that are permanently available
	- ***Post Office Protocol 3***
		- POP3
		- POP client application is something like Mozilla Thunderbird or Outlook
		- establishes unencrypted connection over TCP 110 or secure connection over TCP 995
		- POP3 has messages usually deleted from the mailbox server when downloaded to a local client, but this setting can be changed
	- ***Internet Message Access Protocol (IMAP)***
		- addresses some limitations of POP
		- another mail retrieval program like POP
		- allows permanent connection to the mail server and can connect multiple clients to the same mailbox simultaneously 
		- uses TCP port 143 - insecure
		- secure connections for IMAP-Secure (IMAPS) can be established using TLS over TCP port 993


- ***Directory and Authentication Servers***
	- large enough networks will have separate servers for handling the authentication needed to access resources on the network
	- enterprise network maintain directory servers to manage a centralized database of user accounts 
		- these servers have protocols on them to control network access
		- SSO is a protocol where a user signs in once then gain access to other related applications and services on the network
	- ***Lightweight Directory Access Protocol (LDAP)*** 
		- most network directories are based on X.500 standard
		- TCP/IP protocol used to query an  x.500 directory
		- examples are Windows Active directory or OpenLDAP
		- LDAP  uses TCP/UDP port 389 but can also use TLS to go through TCP port 636 when using LDAPS

- ***Authentication, Authorization, and Accounting***
	- also known as AAA server
		- ***supplicant*** - device requesting access (a given user's computer)
		- ***network access server (NAS) or network access point (NAP)*** -  also known as AAA clients or authenticators - these are network access appliances 
		- ***AAA server*** - the authentication server itself, set within the local network
	- using AAA the switches, routers, etc don't need to store any authentication credentials themselves but rather just transmit this information between the AAA server and the supplicants
	- often implemented using a protocol called ***Remote Authentication Dial In User Service (RADIUS)*** using TCP/UDP port 1812/1813 or as ***Terminal Access Controller Access Control System Plus (TACACS+)*** using TCP port 49. 
		- RADIUS is often  used to authenticate to another network while TACACS is used to authenticate to network appliances 
	- ![[Pasted image 20260119083927.png]]


- ***Remote Terminal Access Servers***
	-  a terminal server allows a host to accept connections to its shell or desktop from across a network - also known as TTY (teletype)
	- ***Secure Shell SSH*** - main way to get secure remote access to UNIX/Linux servers and other network appliances 
		- uses TCP port 22 by default
	- ***Telnet*** - both a protocol and terminal emulation software  tool that transmits shell commands and their output between a client and remote host
		- uses TCP port 23 by default
		- telenet is not encrypted or protected by default, so for sensitive information transmittal use SSH
	- ***Remote Desktop Protocol*** - RDP is Microsoft's protocol for remotely accessing GUI desktops on other Windows machines
		- uses TCP port 3389
		- RDP clients can work for other OSs, allowing you to connect to a Windows device from a non-windows device
		- an open source version of RDP is xrdp

- ***Time Servers***
	- ***Network Time Protocol (NTP)*** - allows networked systems to sync their clocks to a common source
		- allows network and application log entries to show an accurate time of events
		- Stratum levels differentiate the accuracy of network clocks, with the most accurate level being Stratum-0
			- other servers that link to a Stratum-0 source would be Stratum-1
			- Windows  uses the time.windows.com server
		- NTP uses UDP port 123
		- There is ***Network Time Security (NTS)*** - uses TLS encryption to protect time data transfer on TCP port 4460

- ***Network monitoring and management***
	- remote monitoring of devices on a network is essential
	- often uses SSH and RDP
	- ***Simple Network Management Protocol (SNMP)*** - framework for managing and monitoring network devices and incorporates three components: network management system, managed devices, and agents
		- ***agents*** - a process running on a network devices compatible with SNMP
			- agents have a management information database (MIB) holding relevant network statistics 
			- agents can perform a trap operation where it informs the network of certain events such as port failures - the threshold for triggering traps can be set for each value
			- also will poll other agents on the network regarding the MIB of those other agents
		- SNMP works over UDP port 161, and network traps are over UDP port 162
		- SNMPv3 is the current preferred version as it supports authentication between the management system and enrolled devices
		- ![[Pasted image 20260119091437.png]]
	- ***syslog*** - protocol for collecting system logs
		- by default uses UDP port 514
		- ![[Pasted image 20260119091859.png]]
		- syslog messages comprise of a PRI code - a header containing time stamp, a host name, and message
			- the PRI code is calculated from the facility and severity level, with the message portion showing the source process and its content
			- the format of the content is application-dependent