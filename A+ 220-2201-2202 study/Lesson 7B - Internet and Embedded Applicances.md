
•  How does a proxy server work?
•  How does a spam gateway function?
•  How does a load balancer increase the availability of resources?
•  What is the purpose of a unified threat management system?
•  What are several examples of IoT devices?


- ***Proxy Servers*** 
	- on a SOHO network, devices on the LAN use NAT to access the Internet
		- NAT is translating between the private IP address on teh LAN and the publicly addressable IP address configured on the routers WAN interface
	- another option to NAT is ***proxy server*** 
		- proxy servers takes an entire HTTP request from a client, analyzes it, then forwards it to the destination server on the Internet. it does the reverse when a reply comes in 
		- ![[Pasted image 20260119110125.png]]
		- proxy servers configured to use port 8080 by default
	- ***spam gateways and unified threat management***
		- enterprise networks will use specific appliances for portions of their security
			- ***firewalls*** - contain files that are access control lists. traffic that match criteria on those lists is blocked
			- ***intrusion detection systems***  - IDS have scripts that can be used to detect patters of malicious network traffic and alert when a match is made
				- ***Intrusion Protection System*** can be used to block the source of malicious packets 
			- ***virus scanners*** - scan files on the network to detect malware 
			- ***spam gateways*** - SPF, DKIM, DMARC all are used to verify the authenticity of mail servers
				- spam gateways are installed as a network server
			- ***content filters*** - block access to unauthorized sites and services
			- ***data loss prevention (DLP)*** - scans outgoing traffic for data that is marked confidential or otherwise protected. DLP systems can check for whether the transfer is authorized or not
		- ***Unified Threat Management (UTM)*** - enforces a variety of controls and covers a wide variety of security functions

- ***Load Balancer***
	- distributes client requests across multiple servers
		- often these servers provide the same function - web, media, email servers are an example
	- ![[Pasted image 20260119112256.png]]


- ***Supervisory Control and Data Acquisition (SCADA)***
	- deployed in large scale systems with more than one ICS (industrial control system)
	- run on ordinary computers to gather data from a variety of devices around a plant - field devices
		- these field devices will communicate via WAN (cellular or satellite)
		- Legacy and embedded systems are often involved in SCADA, and their age or difficulty with being updated can represent a security risk