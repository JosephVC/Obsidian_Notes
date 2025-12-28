
• What is the purpose of Dynamic Host Configuration Protocol?  
• What are the capabilities of DHCP?  
• What is the purpose of Domain Name System?  
• What is the purpose of VLANs?


- DHCP scope
	- range of IP addresses a DHCP server can offer to client hosts in a particular subnet
	- excludes any addresses that have been configured statically
	- for example, if the range is 192.168.0.100 to 192.168.0.199 there are 100 dynamically addressed hosts on the network

- DHCP leases
	- if the TCP/IP configuration is set to automatically obtain an IP address, a host is set to use DHCP
	- a DHCP client will broadcast DHCPDISCOVER packets to find a DHCP server
		- uses UDP
		- client listens on port 68 and the server on port 67
		- There is no need to configure a DHCP server with more than a static address on the client, as the latter is blasting out port 68 looking for that DHCP server 
	- the server then responds with a DHCPOFFER packet, which will contain relevant information such as default gateway and DNS server address
	- if accepting the offer, the client broadcasts a DHCPREQUEST packet
	- if the server accepts, it responds with a DHCPACK packet
	- the client the broadcasts and ARP message to make sure that the given IP address is still unused - if so it starts using it or declines it and gets a new one
	- the IP address for the client is leased by the server for a limited time, and the client can choose to rebind/renew the ***DHCP lease***
	- ![[Pasted image 20251220152237.png]]

- DHCP reservations
	- 