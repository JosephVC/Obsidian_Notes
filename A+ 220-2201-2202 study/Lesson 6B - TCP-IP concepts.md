
• What are the layers of the TCP/IP model?  
• What are the differences in IPv4 and IPv6?  
• What are the IPv4 classes of addresses?  
• How does DHCP allocate IP addresses and what happens if it fails?

https://www.networkcomputing.com/ip-subnetting/ip-addresses-subnet-masks-and-default-gateways


![[Pasted image 20251123103407.png]]

- Link Layer
	- this layer puts **frames** on the network
	- these frames do not have TCP/IP protocols attached - once you attach that protocol you get an Internet packet
- Internet Layer
	- provides packet addressing and routing within a network of networks - the Internet, basically
	- **Address resolution protocol (ARP)**
		- there needs to be a protocol for handling messages coming in from the Internet layer to devices at the Network interface layer - other devices connected to the network via Ethernet or Wifi
		- ARP allows a host to ask about what MAC address is associated with a given IP address
	- IP does the best it can to deliver packets. it is unreliable and connectionless, so packets might be lost or otherwise damaged/corrupted in transit
- **Transport Layer**
	- **transport control protocol (TCP)** - tries to guarantee forwarding of packets
		- will try to recover or get packets back in order
		- applications using TCP prioritize accuracy in the delivery of information
	- **User datagram protocol (UDP)** - unreliable and connectionless forwarding of packets
		- often  used where speed and immediacy are prioritized, such as media streaming
			- glitches and buffering are better than nothing at all
- **Application Layer**
	- contains various applications and protocols that do things more involved than forwarding packets
		- managing network hosts and operate services
		- TCP/IP suite
			- IPv4 addressing - the core protocol of TCP/IP
				- the IP packet adds headers to whatever data it carries
				- IPv4 is 32 bits grouped into octets and then converted into decimal value
				- network  number (network ID) - common to all hosts on the IP network
				- **Network prefixes ** host number (host ID) - identifies a host on a particular IP network

		  - ***subnet mask*** - a single IP network can be divided into multiple logical subnetworks
			  - we need a subnet mask to know if the source and destination addresses are all on the same network
			  - why do so many network masks start with 255.255.255.0?
				  - that 0 at the end is the host octet and can be given a range of 1-254
				  - the address does not necessarily indicate the network size; class size is not network size
				  - the subnet mask determines which hosts are on the local network and which are outside the network - hosts need to go through a router in order to talk to devices outside the network
				  - slash notation tends to be used for host addresses  while the slash notation tends to be reserved for IP network
				    
			- public and private addresses
				- a host needs a particular public address to communicate online
					- public addresses are set by the ISP, which in turn has to be granted a sufficient number of public IPs for all the computers to communicate with
				- RFC 1918 address are private address and are generally not allowed to route traffic over the public internet
					- ***Class A*** - 0.0.0 - 10.255.255.255
					- ***Class B*** - 16.0.0 - 172.31.255.255
					- ***Class C*** - 168.0.0 - 192.168.255.255
				- to access the internet with a private address you either need a router using ***network address translation (NAT)*** to convert the private to a public address or a proxy server 
				
			- Address classes and default subnet masks
				- the original IP system did not have subnet masks so hosts would identify the network ID just by the address class
				- the default masks are the subnet masks that align with the octet boundaries
				- ![[Pasted image 20251207152748.png]]
			
			- Static v Dynamic Host address configuration
				- static address means someone has to manually configure the address of a given device, and then reconfigure it if other aspects of the network change
					- keep track of the settings for each device
					- in a large organization this would be a huge pain in the ass
					- devices that don't move around like printers and the like are likely to have static IP addresses
				- ***dynamic host configuration protocol (DHCP)*** can provide the IP address, subnet mask, default gateway, and DNS server to a device automatically
				- ***Automatic Private IP Addressing (APIPA)*** - Microsoft technology for when a DHCP server cannot be found
					- APIPA will choose an address between 169.254.0.1 - 169.254.255.254
					- using an APIPA address a computer can communicate with another  device using APIPA but not other networks or hosts that are using DHCP
					- Non-MS or open source methods of the same thing use ***link local*** to accomplish the same thing
					- you can also just not configure an IPv4 address or just use 0.0.0.0


- IPv6 Routing
	- as IPv4 ran out of addresses, there needed to be a new way provide enough address for all devices
	- rather than the 32 bit IPv4 address, IPv6 uses 128 bit addresses using hexadecimal
		- 2001:0db8:0000:0000:0abc:0000:def0:1234
		- you can shorten this by using double colons where there are contiguous sets of 0s
		- the first half of the address is the network ID while the latter half is the Interface ID
		- there is no need for a subnet mask as the network and host portions are a fixed size
	- IPv6 can use multiple address for each interface
	- a global address starts with 2 or 3 in IPv6 hex
	- IPv6 link local addresses - for communicate with neighboring hosts - start with ***fe80***
	- most IPv6 hosts obtain a global and link-local address via local routers
		- this is ***StateLess Address Auto Configuration (SLAAC)*** 
		- no need for a default gateway
		- IPv6 uses a protocol called ***Neighbor Discovery*** - used to implement SLAAC and discover a router, perform interface address querying functions done by ARP in IPv4
	- most hosts and routers can operate both in IPv4 and IPv6 - called dual stack