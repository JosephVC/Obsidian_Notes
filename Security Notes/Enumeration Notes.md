---
---
**Enumeration** is the process of identifying specific attributes of a target - usernames/passwords, network information, etc.

* the reason to do enumeration is to understand a target before testing it
* **useful services to enumerate**
	* DNS - port 53
		* can be used to access bulk domain name translation data through **DNS Zone Transfer**
	* SMTP - port 25
		* while originally used to send email, can also be used to extract email addresses
	* Remote Procedure Calls (RPC) - port 135
		* used to access RPC services;
	* NetBIOS - port 137
		* we can enumerate NetBIOS objects
	* Simple Network Management Protocol (SNMP) - port 161
		* used to handle hosts remotely
	* Lightweight Directory Access Protocol (LDAP) - port 389
		* stores user and group information
	* Server Message Block (SMB) - port 445, runs over TCP
* **Process Context**
	* processes can operate in one of two modes: **user mode or system (aka kernal or supervisor) mode**
	* programs run in their own address space
	* programs use system calls to access system resources
	* **Kernal process and protection rings**
		* run in a privileged mode with access to all services
			* **kernel interrupt**
				* meant for code executed as a result of an interrupt
			* **kernel user**
				* by user request via a system call
		* operating systems provide different levels of access to resources through **protection rings**
			* these rings are arranged in a hierarchy, with ring 0 being kernel level and the highest privilege
			* rings 1 and 2 were often not used, but now get used for hypervisors (virtual machines)
			* ring 3 is generally for user mode
* **Protocols**
	* Internet Protocols - UDP, TCP, ICMP
	* Ethernet
	* API calls
		* NetBIOS
			* allows session-layer services so windows applications on separate computers can communicate with each other over a network
			* more of an API  specification than a protocol
			* NetBIOS Name Service - port 137 UDP
			* Datagram distribution service - port 138 UDP
			* NetBIOS over TCP/IP - port 139 TCP
		* SMB (Sever Message Block)
			* enables shared access to accounts and other services on a network
		* SAMBA
			* Linux implementation of SMB
		* RPC
			* remote procedure call mechanism
			* RPC is interprocess and intersystem
			* client-server operates like a subroutine call
				* the client and server connect through what are called endpoints, which for a programmer look like function calls
			* details are kept out of code
			* Microsoft has its own implementation of this called MSRPC

**Basic Passive Reconns**

|     |     |
| --- | --- |
| Purpose | Commandline Example |
| Lookup WHOIS record | `whois` [tryhackme.com](http://tryhackme.com) |
| Lookup DNS A records | `nslookup -type=A` [tryhackme.com](http://tryhackme.com) |
| Lookup DNS MX records at DNS server | `nslookup -type=MX` [tryhackme.com](http://tryhackme.com)[1.1.1.1](http://1.1.1.1) |
| Lookup DNS TXT records | `nslookup -type=TXT` [tryhackme.com](http://tryhackme.com) |
| Lookup DNS A records | `dig` [tryhackme.com](http://tryhackme.com) `A` |
| Lookup DNS MX records at DNS server | `dig @`[1.1.1.1](http://1.1.1.1)[tryhackme.com](http://tryhackme.com) `MX` |
| Lookup DNS TXT records | `dig` [tryhackme.com](http://tryhackme.com) `TXT` |
