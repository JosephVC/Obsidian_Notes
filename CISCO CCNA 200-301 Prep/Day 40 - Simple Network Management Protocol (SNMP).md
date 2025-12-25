---
---
**Simple Network Management Protocol**

* SNMP is an industry-standard framework and protocol that was originally released in 1988
	* RFC 1065 - structure and identification of management information for TCP/IP based internets
	* RFC 1066 -
	* RFC 1067 - a simple network management protocol
* actually very complex despite the 'simple' in the name
* SNMP can be used to monitor the status of devices, make configuration changes, etc.
* There are two main types of devices in SNMP
	1. **Managed Devices**
		* these are devices being managed using SNMP
			* routers, switches

               2. **Network Management Station (NMS)**

* the device/devices managing the managed devices
* this is the SNMP 'server'

**SNMP Operations**

* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.png]]
* There are three main operations to SNMP
	* managed devices can notify the NMS of events
		* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.1.png]]
	* the NMS can ask the managed devices for information about their current status
		* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.2.png]]
	* the NMS can tell the managed devices to change aspects of their configuration
		* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.3.png]]

SNMP Components

* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.4.png]]
* **SNMP Manager**
	* **listens on UPD port 162**
	* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.5.png]]
	* the software on the NMS that interacts with the managed devices
	* receives notifications, sends requests for information, sends configuration changes, etc.
* **SNMP Application**
	* provides an interface for the network admin to interact with
	* displays alerts, stats, etc.
	* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.6.png]]
* **SNMP Agent**
	* **listens on UDP port 161**
	* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.7.png]]
	* the SNMP software running on the managed devices that interacts with the SNMP Manager on the NMS
	* sends notifications to and receives messages from the NMS
* **Management Information Base (MIB)**
	* structure that contains the variables that are managed by SNMP
	* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.8.png]]
	* each variable is identified with an **Object ID (OID)**
		* **example variables**: interface status, traffic throughput, CPU usage, temperature, etc.

**SNMP OIDs**

* SNMP Object IDs are organized in a hierarchical structure
* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.9.png]]
	

**SNMP Versions**

* Many versions of SNMP have been proposed/developed, but only three of them are in wide-spread use
	* **SNMPv1** - the original version SNMP
	* **SNMPv2c**
		* allows the NMS to retrieve large amounts of information in a single request, so it is more efficient
		* 'c' refers to the 'community strings' used as passwords in SNMPv1, removed in SNMPv2 then added back in SNMPv2c
	* **SNMPv3**
		* much more secure version of SNMP as it supports encryption and authentication; whenever possible, this version should be used

**SNMP Messages**

* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.10.png]]
	* **Read Messages**
		* **Get** - a request sent from the manager to the agent to retrieve the value of a variable (OID), or multiple variables;  the agent will send a **Response** message with the current value of each variable
		* **GetNext -** a request sent from the manager to the agent to **discover the available variables** in MIB
		* **GetBulk** \- A more efficient version of the **NextGen** message (introduced in SNMPv2)
		* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.11.png]]
	* **Write messages**
		* **Set -** a request sent from the manager to the agent to **change the value of one or more variables**; the agent will send a Response message with the new values
			* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.12.png]]
	* **Notification messages**
		* **Trap -** a notification sent from the agent to the manager; the manager does not send a Response message to acknowledge that it received the Trap, so these messages are  'unreliable'
			* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.13.png]]
				
		* **Inform**
			* a notification message that is acknowledge with a Response message
			* originally used for communications between managers, but later updates allow agents to send Inform messages to managers, too
		* **Response**
			* given above

**SNMPv2c Configuration**

* `snmp-server contact --some contact email--` **\= this contact information is entirely optional**
* `snmp-server community --some password--` = configure the SNMP **community strings (i.e. passwords)**
	* **ro = read only = no Set messages**
	* **rw = read/write = can use Set messages**
* `snmp-server host --ip address-- version --whatever version you run-- --your password--`  = specify NMS, version, and community
* `snmp-server enable traps snmp linkdown linkup`
* `snmp-server enable traps config`
	* both the above configure trap types
* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.14.png]]
* In SNMPv1 and SNMPv2, there is no encryption.  The community and message contents are sent in plain-text.  This is not secure, as the packets can easily be captured and read

**QUIZ**

* Which of the following SHMP messages are used by NMS to 'read' information from the managed devices?
	* D, G

* Which SHMP messages are sent to UDP port 162
	* trap and inform messages are sent from the managed devices, thus are sent on UDP port 162

* Which of the following SNMP message types was introduced in SNMPv2 and allows mass-retrieval of information from managed devices?
	* GetBulk

* Which of the following pieces of software runs on an SHMP NMS?
	* the Manager
		* interacts with the SHMP agent on the managed devices

* Which SHMP messages are sent without expecting a Response
	* Trap

![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.15.png]]

* GetNext, Get
* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.16.png]]
* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.17.png]]
* ![[./_resources/Day_40_-_Simple_Network_Management_Protocol_(SNMP).resources/image.18.png]]
