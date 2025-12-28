---
---
* DTP and VTP were removed from the latest version of the CCNA, but questions on them might still pop up

**DTP (Dynamic Trunking Protocol)**

* DTP is a Cisco proprietary protocol that allows Cisco switches to **dynamically determine their interface status** (**access** or **trunk)** without manual configuration
* DTP is enabled by default on all Cisco switch interfaces
* so far we've manually configured switchports using these commands
	* `switchport mode access`  OR `switchport mode trunk`
* for security purposes, manual configuration is recommended.  DTP should be disabled on all switchports
	* DTP has certain security concerns
* using the `switchport mode ?` command, we get a list of options
	* the `dynamic` option is DTP
	* ![[./_resources/Day_19_-_DTPVTP.resources/image.png]]
		* a switchport in **dynamic desirable** mode will actively try to form a trunk with other Cisco switches.  It will form  a trunk if connected to another switchport in the following modes
			* `switchport mode trunk`
				* two switches connected via the same interface will both agree to act as a trunk
			* `switchport mode dynamic desirable`
				* like the above, both switches fill form a trunk
			* `switchport mode dynamic auto`
				* a switchport in this mode does not automatically try to form a trunk, but will passively form a trunk if the other switch wants to
		* ![[./_resources/Day_19_-_DTPVTP.resources/image.1.png]]
		* a switchport in **dynamic auto mode** will not actively try to form a trunk with other Cisco switches, however it will form a trunk if the switch connected to it is actively trying to form a trunk; it will form  a trunk with a switchport in the following modes:
			* **switchport mode trunk**
			* **switchport mode dynamic desirable**
* ![[./_resources/Day_19_-_DTPVTP.resources/image.2.png]]
* DTP will not form a trunk with a router, PC, etc.  The switchport will be in access mode.
* on older switches, `switchport mode dynamic desirable` is the default administrative mode
* on newer `switchport mode dynamic auto` is the default administrative mode
* you can disable DTP negotiation on an interface with the `switchport nonegotiate` command
* configuring an access port `switchport mode access` also disables DTP negotiation on an interface
* switches that support 802.1Q and ISL trunk encapsulations can use DTP to negotiate the encapsulation they will use
* this negotiation is enabled by default, as the default trunk encapsulation mode is `switchport trunk encapsulation negotiate`
* ISL is favored over 802.1Q, so if both switches support ISL it will be selected
* DTP frames are sent in VLAN1 when using ISL, or in the native VLAN when using 802.1Q (the default native VLAN is VLAN1, however)

**VTP (VLAN Trunking Protocol)**

* **VTP** allows you to configure VLANs on a central VTP server switch, and other switches (VTP clients) will synchronize their VLAN databases to the server
* it is designed for large networks with many VLANs, so you don't have to configure each VLAN on every switch
* it is recommended to not be used, and in rarely used in practice
* There are three VTP versions, 1,2, 3
* there are three VTP modes: **server, client, transparent**
	* **Servers**
		* can add/modify/delete VLANs
		* store VLAN database in non-volatile RAM (NVRAM)
		* will increase **revision number** every time a VLAN is added/modified/or deleted
		* will advertise the latest version of the VLAN on its trunk interfaces, and the VTP
		* **VTP servers also function as VTP clients**
			* **a VTP server will synchronize to another VTP server with a higher revision number**
		* **VTP clients**
			* cannot add/modify/delete VLANs
			* do not store the VLAN database in NVRAM (in **VTP3** they do)
			* will synchronize their VLAN database to the server with the highest revision number in their VTP domain
			* will advertise their VLAN database and forward VTP advertisements to other clients over their trunk ports
* Cisco switches operate in VTP server mode by default
* ![[./_resources/Day_19_-_DTPVTP.resources/image.3.png]]
* one danger of VTP is that if you connect an old switch with a higher revision number to your network (and the VTP domain name matches), all switches in the domain will sync their VLAN database to that switch
	* ![[./_resources/Day_19_-_DTPVTP.resources/image.4.png]]
* VLAN Transparent mode
	* does not participate in the VTP domain (does not sync its VLAN database)
	* Maintains its own VLAN database in NVRAM.  it can add/modify/delete VLANs but they won't be advertised to other switches
	* will forward VTP advertisements that are in the same domain as it
* changing the VTP domain to an unused domain will reset the revision number to 0
* changing the VTP mode to transparent will also reset the revision number to 0
