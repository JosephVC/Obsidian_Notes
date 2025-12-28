---
---
**Port Security**

* this is a security feature of Cisco switches
* it allows you to control which source MAC addresses are allowed to enter the switchport
* if an unauthorized source MAC address enters the port, an action will be taken
	* the default action is to place the interface in an **'err disabled'** state
* ![[./_resources/Day_49_-_Port_Security.resources/unknown_filename.png]]

* when you enable port security on an interface with the default settings, one MAC address is allowed
	* you can manually configure the max. number of MAC addresses
	* if not configured manually the switch will allow the **first source MAC address that enters the interface**
* you can change the max. number of MAC addresses allowed
	* a combination of manually configured MAC addresses and dynamically learned addresses is possible
		* ![[./_resources/Day_49_-_Port_Security.resources/image.png]]
			

**Why port security?**

* port security allows network admins to control which devices are allowed to access the network
* MAC address spoofing is simple, though
	* it's easy to configure a device to send frames with a different source MAC address
* rather than manually specify the MAC addresses allowed on each port, port security's ability to limit the number of MAC addresses allowed on an interface is more useful
* consider the DHCP starvation attack
	* thousands of fake MAC addresses are spoofed
	* the DHCP server assigned IP addresses to every fake MAC address, thus exhausting the DHCP pool
	* the MAC address table of a switch can also become full due to such an attack
* limiting the number of MAC addresses on an interface can limit such attacks

**Enabling Port Security**

* ![[./_resources/Day_49_-_Port_Security.resources/image.1.png]]
* ![[./_resources/Day_49_-_Port_Security.resources/image.2.png]]
* ![[./_resources/Day_49_-_Port_Security.resources/image.3.png]]
* ![[./_resources/Day_49_-_Port_Security.resources/image.4.png]]
* ![[./_resources/Day_49_-_Port_Security.resources/image.5.png]]
	* **step one:** disconnect the unauthorized device and either manually reenable the interface or let **errdisable** recovery do it automatically

**Violation Modes**

* there are three different violation modes that determine what a switch will do if an authorized frame enters an interface configured with port security
	* **shutdown**
		* effectively shuts down the port by placing it in an err-disabled state
		* generates a syslog and/or SNMP message when the interface is disabled
		* the violation counter is set to 1 when the interface is disabled
	* **restrict**
		* the switch discards traffic from unauthorized MAC addresses
		* the interface is NOT disabled
		* Generates a Syslog and or SNMP message each time an unauthorized MAC is detected
		* the violation counter is incremented by 1 for each unauthorized frame
		* ![[./_resources/Day_49_-_Port_Security.resources/image.6.png]]
			
	* **Protect**
		* the switch discards traffic from unauthorized MAC addresses
		* the interface is NOT disabled
		* it does NOT generate Syslog/SNMP messages for unauthorized traffic
		* it does NOT increment the violation counter
		* ![[./_resources/Day_49_-_Port_Security.resources/image.7.png]]
			

**Secure MAC address aging**

* ![[./_resources/Day_49_-_Port_Security.resources/image.8.png]]
* by default a secure MAC address will not **age out** (their **aging time** will be 0)
	* can be incorporated with **switchport port-security aging time _minutes_**
* the default aging type is **absolute**
	* **absolute:**  after the secure MAC address is learned, the aging timer starts and the MAC is removed after the timer expires, even if the switch continues receiving frames from the source MAC address
	* **inactivity:** after the secure MAC address is learned, the aging timer starts but is reset ever time a frame from that source MAC address is received on the interface
	* the **aging type** is configured with **switchport port-security aging type {absolute | inactivity}**
	* secure static MAC aging (addresses configured with **switchport port-security mac-address _x.x.x_)**is disabled by default
		* can be enabled with **switchport port-security aging static**
* ![[./_resources/Day_49_-_Port_Security.resources/image.9.png]]

**Sticky Secure MAC Addresses**

* **'sticky' secure MAC addresses** learning can be enabled with the following command
	* **switchport port-security mac-address sticky**
* when enabled, dynamically-learned secure MAC addresses will be added to the running config like
	* **switchport port-security mac-address sticky _mac-address_**
* the 'sticky' secure MAC addresses will never age out
	* you need to save the running-config to the startup-config to make them truly permanent if the switch restarts
* when you issue the **switchport port-security mac-address sticky** command, all current dynamically-learned secure MAC addresses will be converted to sticky secure MAC address
* if you issue the **no switchport port-security mac-address sticky** command, all current sticky secure MAC addresses will be converted to regular dynamically-learned secure MAC addresses
* ![[./_resources/Day_49_-_Port_Security.resources/image.10.png]]

**MAC Address Table**

* secure MAC addresses will be added to the MAC address table like any other MAC addresses
	* sticky and static secure MAC addresses will have a type of STATIC
	* dynamically-learned secure MAC addresses will have a type of DYNAMIC
	* all secure MAC addresses can be viewed with **show mac address-table secure**
	* ![[./_resources/Day_49_-_Port_Security.resources/image.11.png]]

**Command Review**
![[./_resources/Day_49_-_Port_Security.resources/image.12.png]]

**QUIZ**

![[./_resources/Day_49_-_Port_Security.resources/image.13.png]]

* C
	sticky MAC addresses are dynamically learned
	

![[./_resources/Day_49_-_Port_Security.resources/image.14.png]]

* b, e

![[./_resources/Day_49_-_Port_Security.resources/image.15.png]]

* A
	* because the **violation** **mode** is **protect**, all unauthorized traffic will be dropped, but authorized frames will still be forwarded as the interface will not be in an **err disabled** state

![[./_resources/Day_49_-_Port_Security.resources/image.16.png]]

* a, b
	* unplugging alone does not necessarily re-enable the interface; **you should unplug the device before preforming the steps in A or B**

![[./_resources/Day_49_-_Port_Security.resources/image.17.png]]

* a
	* the admin mode is **static access** so the command is accepted

![[./_resources/Day_49_-_Port_Security.resources/image.18.png]]

* C, E
	* static addresses **can** be configured
	* SW1 will only drop **unauthorized** packets
	* previously learned addresses **will not** be removed
	* according to the default settings, just one host will be allowed
* ![[./_resources/Day_49_-_Port_Security.resources/image.19.png]]
* ![[./_resources/Day_49_-_Port_Security.resources/image.20.png]]
