---
---
**Layer 2 Discovery Protocols**

* L2 discovery protocols like CDP and LLDP share information with and discover information about neighboring (connected) devices
* the shared information includes host name, IP address, device type, etc.
* CDP is a Cisco proprietary protocol
* LLDP is an industry standard protocol (IEEE 802.1AB)
* these protocols can be considered a security risk as they share information about devices on the network; certain workplaces may want these protocols disabled

**Cisco Discovery Protocol (CDP)**

* CDP is a Cisco proprietary protocol
* CDP is enabled by default on Cisco devices by default
* CDP messages are periodically sent to multicast MAC address 0100.0CCC.CCCC
* when a device receives a CDP message, it processes and discards the message.  It does NOT forward it to other devices
* **by default, CDP messages are sent once every 60 seconds**
* **by default, CDP holdtime is 180 seconds;** if a message isn't received from a neighbor for 180 seconds the neighbor is removed from the CDP neighbor table
* CDPv2 messages are sent by default
* **key commands**
	* `show cdp`
	* `show cdp traffic`
	* `show cdp interface`
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.png]]
* the CDP neighbor table
	* `show cdp neighbors`
	* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.1.png]]
		* each time a router receives a CDP message, the Holdtime will reset to 180; if the countdown gets to 0, the neighbor will be removed from the CDP neighbor table
	* the command `show cdp neighbors detail` gives you greater detail into the CDP neighbor table
		* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.2.png]]
	* to show information for a specified neighbor use the command `show cdp entry --some device--`
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.3.png]]

**CDP Configuration Commands**

* CDP is globally enabled by default
* CDP is also enabled on each interface by default
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.4.png]]

**Link Layer Discovery Protocol**

* LLDP is an industry standard protocol
* usually disabled on Cisco devices by default, so must be manually enabled
* a device can run CDP and LLDP at the same time
* LLDP messages are periodically sent to multicast MAC address 0180.C200.000E
* when a device receives an LLDP message, it processes and discards the message; it does NOT forward it to other devices
* by default, LLDP messages are sent once every **30 seconds**
* LLDP holdtime is 120 seconds
* LLDP has an additional timer called the **reinitialization** **delay**.,  if LLDP is enabled (globally or on an interface) this timer will delay the actual initialization of LLDP; **2 seconds** by default

**LLDP Configuration Commands**

* LLDP is usually globally disabled by default
* LLDP is also disabled on each interface by default
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.5.png]]
	

**LLDP Protocol**

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.6.png]]
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.7.png]]

**QUIZ**

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.8.png]]
	* a), c

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.9.png]]
	* C), D)

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.10.png]]
	* B)
		* because SW1 is a multilayer switch, it has the capabilities of both a switch and a router
			* B stands for Bridge, which is  a term that can be used interchangeably with switch

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.11.png]]
	* b, f

* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.12.png]]
	* b)

![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.13.png]]

* b, c, e, f
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.14.png]]
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.15.png]]
* ![[./_resources/Day_36_-_L2_Discovery_Protocol_(CDP_&_LLDP).resources/image.16.png]]
