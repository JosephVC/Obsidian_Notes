• What is a network that covers the area equivalent to a city known as?  
• A user has connected a smartwatch and earbuds to their cellphone over Bluetooth. What  
type of network have they created?  
• You have been tasked with creating a network in which each segment of the network is  
designed as a modular function. What type of network are you creating?  
• What is a whole site that is dedicated to provisioning server resources called?  
• Which IEEE ethernet standards are most cabled LANs based on?


- LAN - Local Area Network
	- group of computers connected by cabling and one or more network switches within a given geographical area
	- might be a single floor or a whole building 
	- any network where the nodes are within 1-2km are local
	- owned and managed by the company that uses the network
	- • 100BASE-T refers to Fast Ethernet over copper twisted pair cabling. Fast Ethernet works at
     • 100BASE-T refers to Fast Ethernet over copper twisted pair cabling. Fast Ethernet works at
        100 Mbps.
     • 1000BASE-T refers to Gigabit Ethernet over copper twisted pair cabling. Gigabit Ethernet
		works at 1000 Mbps (or 1 Gbps). 1000BASE-T is the mainstream choice of standard for most
		LANs.
	 • 10GBASE-T refers to a copper cabling standard working at 10 Gbps.

- WAN - Wide Area Network
	- spans multiple geographic areas
	- the Internet is an example
		- your ISP is an organization that facilitates access to the Internet from a LAN
	- an org. can use a WAN to connect multiple LAN

- WLAN - Wireless LAN
	- most modern wireless LANs use 802.11 standard - wifi

- MAN - Metropolitan Area Network
	- managed by a city or municipality 

- PAN - Personal area Network
	- connecting devices over a few meters
	- can share data between devices
	- bluetooth is an example of a PAN

- Storage Area Network
	- network of storage devices
	- must be attached to a dedicated network independent of the LAN
		- this makes sure the SAN traffic does not interfere with the LAN traffic
	- SAN data is transferred in chunks of data with no other file system structure
	- various different types of storage solutions are consolidated on the SAN
	- uses high speed connections like Fibre Channel or iSCSI for data transfer
		- Fibre Channel
			- high speed network dedicated to servers to SANs
			- https://www.geeksforgeeks.org/computer-networks/fundamentals-of-fibre-channel/
				- uses point to point technology
					- a single link connects two ports
				- fibre channel arbitrated loop
				- switched fabric topology
					- storage devices are connected to a switch, and the switches are connected via a port to each other. one port on the connected switches is then connected to a server
		- iSCSI
			- Internet Small Computer System Interface
			- works on top of TCP and allows SCSI commands to be sent end-to-end over LANs and WANs