

•  What is the purpose of Dynamic Host Configuration Protocol?
•  What are the capabilities of DHCP?
•  What is the purpose of Domain Name System?
•  What is the purpose of VLANs?


- ***DHCP function***
	- DHCP servers can be used to adjust for installation errors regarding networking

- ***DHCP Scope***
	- the range of IP addresses the DHCP server can offer hosts in a subnet
	- ignore addresses that have been statically configured
	- you effectively tell a host to use DHCP by that it should automatically obtain an IP address
	- ![[Pasted image 20260103152354.png]]

- DHCP Reservations
	- the DHCP server will have a list of MAC address for devices that receive the same IP address 

-  Domain name system
	- a host name is configured when an OS is installed on a host
	- to prevent the potential for duplicate host names on a network, you can combine the host name with the domain name and suffix - toyota.auto.car
		-  the host name is toyota and the domain name + suffix is "auto.car"
	- the ***Fully Qualified Domain Name FQDN*** is the 'toyota.auto.car'
	- DNS is used to assign the above FQDN
	- the top of the DNS hierarchy is the root, which is just a period (.)
		- there are 13 root severs, A-M
	- below the root domain are the top level domains (TLDs)
		- such as .com, .net, blah blah blah
	- ![[Pasted image 20260103154215.png]]


- ***DNS Queries***
	- a client needs to get the appropriate DNS record in order to resolve a host or domain name to an IP address
	- when typing in a domain name, a client app - web browser or 'stub resolver' - will check its own DNS cache for the IP address
		- if no mapping is found, the stub  will query a local DNS server, whose IP address are set in the TCP configuration
		- ***communication with DNS servers is over port 53***
	- ![[Pasted image 20260103155003.png]]

- DNS Record types
	- a DNS server responsible for a given region will have a variety of resource records that will help the server resolve names into IP addresses
	- these records can be updated or created manually or dynamically based on information received from clients and servers on the network
	- ***Address (A) and Address (AAAA) records***
		- the A record is used to resolve a  host name to an IPv4 address where a AAAA record resolves a host name to an IPv6 address
	- ***CNAME Record***
		- canonically named record
		- used to  link one domain name to another domain name
		- if two entities merge, rather than maintain two separate websites a CNAME record can be made that links the two sites
		- this allows someone going to one site to be automatically redirected to the other entity's site
	- ***Mail Exchanger (MX) Resource Records***
		- used to identify an email server for the domain so that other servers can send messages to it
		- in an organization with multiple servers, each server has an MX record
		- each MX server is given a preference value, where the lowest value is preferred
		- the host name in an MX record must identify whether it has an A or AAAA record
	- ***DNS Spam Management Record***
		- a TXT record is used to store any free form  text that might be needed to support other network services
		- a single domain service will likely have a  lot of these records, which are often  used to verify spam services and block transmissions of spoofed/unwanted messages
	- ***sender Policy framework*** (SPF)
		- uses txt resource records published via DNS by an organizer's hosting email service
		- there is only one SPF record per domain
		- identifies hosts authorized to send mail from a domain
		- can also tell what to do for mail from servers NOT on the list
	- ***DomainKeys identified***
		- DKIM
		- uses cryptography to validate the source server for a given email message
		- can replace or supplement SPF
		- configuring DKIM requires an  organization to upload a txt recod of their public encryption key to the DNS server
		- the above key is used by organizations receiving mail from the server to verify the authenticity of the domain
	- ***Domain-Based Message Authentication, Reporting, and Conformance
		- DMARC
		- ensures that DKIM and SPF is used effectively - can  use ooth or either one
		- DMARC policy is published as a txt record on the DNS srever
		- DMARC authentication failures can be reported to the sender
	- ***Virtual LANs*** (virtual local area network)
		- all hosts connected to the same switch are said to be in the same broadcast domain
		- larger networks can have thousands of ports hosts to manage, and when all of these hosts are on the same domain overall performance can degrade
		- managed switches allow a group of ports to be divided into groups using a feature called VLANs
			- large networks can be logically divided and network security can be potentially increased
		- VLANs have IDs from 2 to 4094, with VLAN 1 being the default VLAN
			- unless configured differently, all ports on a managed switch default to being in VLAN 1
		- The simplest means of assigning a node to a VLAN is by configuring the port interface on the switch with a VLAN ID in the range 2 to 4094. For example, switch ports 5 through 8 could be configured as a VLAN with the ID 100, and ports 9 through 12 could be assigned to VLAN 200. Host A connected to port 2 would be in VLAN 100, and host B connected to port 12 would be in VLAN 200.
	- ***Virtual Private Network***
		- allows hosts to connect to a LAN without physically being active at the site
			- rather than connect to a switch, a host connects via remote access through the Internet - thus VPNs need to be very secure
		- ![[Pasted image 20260118110954.png]]
		- 