
• What computer component is responsible for establishing the physical connection to the  
network?  
• What are the first 24 bits of a MAC address known as?  
• What is the cable that runs from the wall port through the walls terminated into?  
• Which type of switch can perform its function without requiring any sort of configuration?  
• Which PoE standard provides approximately 51W of power?


- most Network Interface Cards (NICS) support 1000Base T ethernet

- MAC address
	- first 24 bits are the OUI - Organizationally Unique Identifier
		- identifies the manufacturer 
	- last 24 bits identify the specific NIC being used


- Patch Panels
	- the cabling running from an office computer goes to a wall port and then to a patch panel
	- one type of panel has you split open an punch down the individual wires in the ethernet cable and another is pre-wired with RJ45 cables


- Ethernet Switches
	- used to connect multiple devices in a network together
	- the switch provisions one port for each device needing to connect to the network
	- when connected, the device's MAC address is added to the switch's MAC address table and the switch keeps track of what port the device is connected to
		- when a frame comes in, the switch can then decode each frame and identify the proper port and MAC address to forward it to
	- ![[Pasted image 20251116095439.png]]
	- each switch port is considered its own collision domain and each computer connected to it has a full duplex connection to the network, meaning it can simultaneously send and receive data at full speed. 
	- an **unmanaged switch** does its job without requiring any sort of configuration; just power it on and connect things to it
		- mainly for small networks with up to 4 to 8 devices
		- basically the devices an ISP will hand out to home users
	- a **managed switch** is for larger setups and will allow for configuration but can be unmanaged out of the box
		- made to be bolted to racks
		- usually come with 24-48 access ports and can be connected to other switches
		- the top row are odd number ports and the bottom are even
	- a **modular switch** have power supplies and allow fast communication backplane to interconnect multiple other switches, allowing hundreds of access ports via a single networking device
		- backplane - 
		- ![[Pasted image 20251116101026.png]]

- Power over Ethernet (PoE)
	- the type of PoE switch that provides the PoE is the **power source equipment, or PSA**
	- this supplies power to devices via an ethernet cable
	- 802.3af (type 1 or 2-pair PoE) - allows up to 13W (350mA@48v ) and limited to 15.4W but power drops over max. 100m of cable
		- phones, basic wifi access points and other basic devices can use this
	- 802.3at (PoE+ or type 2 PoE) allows up to 25W with max current of 600mA
		- bigger wifi devices, cameras and video IP phones will use this
	- 802.3bt (PoE++, type 3 and type 4 PoE, 4PPoE) - up to 51W for type 3 and 73W for type 4
		- LEDs, signage, POS systems, or other higher power devices will use this
	- PoE Switch
		- referred as endspan power sourcing equipment (PSE)
			- **endspan** is where the switch will detect whether the end device is PoE or not, and then automatically enables power
			- the **midspan** is where you add a device in between the PSA and the given device needing power - this is also called a **PoE injector**
	- PoE is considered more efficient than using a wall socket
	- PoE cables should not exceed 100m