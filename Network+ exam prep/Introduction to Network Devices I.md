---
---
**Layer 1 devices**

* **OSI Model (Open Systems Interconnection)**
	* created to allow disparate computing systems to communicate with each other
	* Seven Layers
		* 7.  Application
		* 6.  Presentation
		* 5.  Session
		* 4.  Transport
		* 3.  Network
		* 2.  Data Link
		* 1.  Physical
* the **analog modem**
	* word is comprised of a combination of modulator/demodulator
	* a digital signal coming from a digital node was converted to an analog signal to be sent along wires (physical layer of OSI), and vice versa
	* meant to create connections between network segments along the public switched telephone network (PSTN) via POTS (Plain Old Telephone System)
	* provide a single connection to a network
* the **hub**
	* acts as a concentrator/repeater and does not care about the origin or destination of the signal
		* a signal arriving on one port is replicated out all the other ports
		* not very common in modern networking

**Layer 2 devices**

* **the switch**
	* uses an ASIC (Application Specific Integrated Chip)
	* programs allow the ASIC to know when a device is on the network and which port it's connected to via the given device's MAC address
	* may have a few or many ports
	* can be very simple or complex and programmable
	* will only communicate with the local network devices
* the **WAP (Wireless Access Point)**
	* a specific kind of network bridge that connects (bridges) wireless segments with wired network segments
		* most common type bridges 802.11 wifi with 802.3 Ethernet network
	* will only communicate with local network devices

**Layer 3 devices**

*     **MLS (Multi Layer Switch)**
	* will provide normal layer 2 network switching services, but will also provide  Layer 3 or higher OSI model services
	* the most common MLS switch is a layer 3
	* programmed to handle both switching and routing functions; allows device to pass data to non-local network devices
	* highly programmable and complex device
		* these are expensive and are more likely to be found in enterprise environments rather than in the home
	* may have a few or many ports
* **Router**
	* uses Layer 3 network information to connect different networks together
	* uses software programming vs dedicated chip 
		* this programming allows the router to find the best possible route to all the networks it keeps track of
	* can connect to local and non-local networks
