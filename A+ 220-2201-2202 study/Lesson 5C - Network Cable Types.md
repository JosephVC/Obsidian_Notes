
 • What type of network cable should be used in environments with high levels of external  
interference?  
• Which ethernet Cat standard can provide a maximum transfer rate of 25 Gbps over a  
maximum distance of 30 meters?  
• What type of connector does a Cat 7 cable use?  
• What is the order of wires in a T568B cable?  
• Which tool is used to fix a RJ45 jack to a patch cord?  
• Which cable type transfers data using light?


- Unshielded Twisted Pair (UTP)
	- most popular type of network cable
	- made of four copper wire pairs
	- wire pairs are twisted around each other to reduce electrical interference
		- LINK TO HOME WIRIING EXPLANATION 
	- wire pairs send a balanced signal, meaning each wire carries equal but opposite signal from the other one - this also helps reduce interference
	- attenuation is a problem, meaning the signal loses strength over long ranges
	- Max recommended distance for UTP is 100m

- Shielded Twisted Pair (STP)
	- provides extra protection against interference
	- usually required in situations with strong sources of electrical interference 
	- **foiled unshielded twisted pair (F/UTP)** has a single foil shield around all the wires in the cable
	- can also be called screen twisted pair (ScTP) or foil twisted pair
	- provides decent protection against interference and crosstalk
	- **Shielded Foiled Twisted Pair (S/FTP)** has a braided outer shield and foil-shielded pairs
		- as each pair is foil shielded this is the best protection
		- expensive and less flexible than other variants
	- **unshielded w/foil twisted pair (U/FTP)** - no outer shield but each wire pair has foil around them. provides good protection
	- the screen material must be properly bonded to the connector to prevent the metal from acting like an antenna and generating its own interference - modern cables include this bonding within the cable design


- Ethernet CAT standards
	- ![[Pasted image 20251116140730.png]]
	- ![[Pasted image 20251116140748.png]]

- RJ 45 connector
	- ![[Pasted image 20251116142506.png]]
		- two methods of terminating twisted pair - T568A/T568B
			- T568A - pin 1 is wired to green/white, pin 2 is wired to green, pin 3 is wired to orange/white, and pin 6 is wired to orange.
			- T568B - the position of the green and orange pairs is swapped over, so that orange terminates to 1 and 2 and green to 3 and 6
			- straight through Ethernet cable is wired with the same type of termination at both ends
			- RJ11 is another port end used for things like telephone cable

- Installation
	- installation must be compliant with local building regulations and fire codes
	- wiring will often be run through a **plenum space** that will also be shared by HVAC and other building systems
		- as fire can also run through the plenum space, you want to make sure the cabling can withstand heat from fire and other heating elements in the space
		- plenum cable must emit minimal smoke and also extinguish itself
		- plenum cables will use treat PVC or FEP jackets and insulation. this makes the cable less flexible. these cables will be marked CMP on the jacket. standard cables are marked CMG or CM
	- with most office cabling, a patch cord is used between a device and the wall port
	- behind the wall port, a permanent cable is run through the wall and ceiling to the IDF/equipment room and connected to a patch panel
	- the given port on the patch panel is then connected to the switch
	- the patch cable is terminated with RJ45 connectors while the permanent cable is connected to the patch panel via **insulation displacement connectors (IDC) or punchdown blocks**
		- in a punchdown block, the ethernet cable is separated into its individual wire pairs and punched down into the slots in the IDC using a **punchdown tool** 
	- permanent cords use solid cable with thicker wires while patch cords use stranded cable with thinner wire for added flexibility
	- the 100m distance limitation is for the whole link or the **channel link**
	- each patch cord should only be up to 5m long
	- when done with terminating the ethernet cable, make sure to test it with a **cable tester**
	- you can use a **tone generator** to identify cables before installation or after you disconnect them
	- a **loopback adaptor** tests and NIC or switch port
		- you can make your own with some patch cable where the wires connect pin 1 to pin 3 and pin 2 to pin 6. when you connect the loopback plug to a port you see a solid link LED showing the port can send and receive
			- this will likely not work with gigabit ethernet ports. for that you will need another tester
			- ![[Pasted image 20251116151550.png]]
	- ****


- network taps - used to analyze the signals on a cable and send them to a packet or protocol analyzer. they are either powered or unpowered
	- passive test access point (TAP) - a box with ports for incoming and outgoing cables
		- has an inductor that copies the signal from the cables, even if the frames are corrupt
		- gigabit networking is too complex for a passive tap
	- Active tap - performs signal regeneration

- Direct Burial - Outside Plant ( OSP )
	- run on external walls of buildings or between buildings
		- Arial cable is strung between two anchors and is vulnerable to UV rays and other weathering
		- buried cables are exposed to temperature extremes and dampness, so regular PVC cable cannot be used
		- **direct burial cable** is laid and the covered in earth or cement/concrete; can be armored to protect against rodents chewing on it
	- OSP cable housing will often be gel filled to protect against temperature extremes

- Optical cabling
	- does not suffer from electrical interference and is less susceptible to attenuation
	- supports higher bandwidth and longer cable runs (miles rather than meters)
	- consists of ultra fine glass core
	- surrounded by more glass, ceramic, or plastic cladding which guides light pulses along the core
		- the cladding also has a protective coating called a buffer
	- **single mode fiber (SMF)** - small core (8-10 microns) and is designed to carry a long wavelength of infrared signal generated by a high power concentrated laser diode
		- supports data rates up to 10gbps or better and cable runs of many kilometer, depending on the quality of the cable and optics
	- **multimode fiber (MMF)** - meant to carry a shorter wavelength of light
		- uses less expensive LEDs to generate light and is thus less expensive overall to deploy
		- does not support the high speeds of single mode fiber nor can go for as long a distance as single mode
		- better suited for LANs than WANs
	- **straight tip connector (ST)** - bayonet-style connector that uses a push and twist locking mechanism; mostly for older multi-mode networks
	- **subscriber connection (SC)** - push/pull design for easier use
		- there are simplex and duplex versions of this (two simplex clipped together)
		- ![[Pasted image 20251122153659.png]]
		- 
	- **Lucent connector (LC)** - small form factor connector with tabbed push pull design. smaller than SC to allow for greater density of ports
		- little connector or local connector
		- ![[Pasted image 20251122153724.png]]
		- 

- **Coaxial Cabling** 
	- to cancel out interference two conductors in line with the same axis are used
		- the core signal conductor is enclosed by a dielectric (non conducting) material and then a wire mesh is wrapped around both
			- the wire mesh is both EMI shielding and ground
		- ![[Pasted image 20251122154846.png]]
		- mainly uses and F type connector
			- ![[Pasted image 20251122154926.png]]
			- 