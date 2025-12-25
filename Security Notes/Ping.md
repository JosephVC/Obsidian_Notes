---
---
You ping in order to test whether a connection to a remote resource is possible.  the latter could be a computer or website

Ping works on the ICMP protocol, which is a TCP/IP protocol

* this works on the **Network** layer of the OSI model and thus the **Internet** layer of the TCP/IP model
* the basic syntax is **ping <target>**
	* **ping <target> -4** returns IPV4, while **\-6** returns IPV6
	* **ping -i** allows you to set the interval of sent ping requests 
	* **ping -v** gives a more verbose output
