---
---
**The Purpose of DHCP**

* DHCP allows a host to dynamically/automatically learn various aspects of its network configuration - IP address, subnet mask, default gateway, DNS server, etc. without manual/static configuration
* **It is essential to modern networking** as it leaves knowing specific aspects of network configuration up to the device rather than the user
	* in larger networks, DHCP is crucial
* typically used for client devices - PCs, phones, etc.
* devices such as routers, switches, ec.
* in small networks, - home networks - the router typically acts as DHCP server for the various hosts
* in larger networks, the DHCP server is likely a Windows/Linux server

**The Basic Functions of DHCP**

* A **Preferred IP address** means the PC was previously assigned this IP address by the DHCP server, so it asked to receive the same address again next time
* DHCP servers **lease  IP addresses** to clients; these leases are usually not permanent, and the client must give up the address at the end of the lease
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.png]]
* on a home network, the router may provide a variety of serves, such as being the default gateway, DNS server, and DHCP server

**DHCP Release**

* the `ipconfig /release` command allows you to release an IP address
* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.1.png]]
	* the above will release the current IP server
* DCHP **servers** use UDP 67
* DHCP **clients** use UDP 68
* **DHCP release message:**
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.2.png]]
		* Can be sent using unicast
		* **What is the magic cookie?**

**Four messages involved in gaining a new IP address from the DHCP server**

* DHCP Discover
	* a broadcast message from the client
	* asking if there are DHCP servers in the network, asking if they have an IP address
* DHCP Offer
	* this message can either be **broadcast** or **unicast**
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.3.png]]
* DHCP Request
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.4.png]]
		
* DHCP Ack
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.5.png]]
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.6.png]]
		* DHCP Ack can be broadcast or unicast

* DHCP Relay
	* Some network engineers might choose to configure each router to act as the DHCP server for its connected LANs
	* large enterprises often choose to use a centralized DHCP server
		* a centralized server won't receive the DHCP client's broadcast DHCP messages, as broadcast messages don't leave the local subnet)
			* to fix this, you can configure a router to act as a **DHCP relay agent**
			* the router will forward the client's broadcast DHCP messages to the remote to the remote DHCP server as unicast messages
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.7.png]]

**DHCP Server Configuration in IOS**

* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.8.png]]
	* an **infinite lease** is not recommended
* **DHCP binding**
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.9.png]]
* **Configure router as a DHCP Relay agent**
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.10.png]]

**DHCP Client Configuration Mode in IOS**

* `ip address dhcp` mode to tell the router to use DHCP to learn its IP address
* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.11.png]]

**Command Summary**

* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.12.png]]

**QUIZ**

* what is the correct order of messages when a DHCP client gets an IP address from a server
	* Discover, Offer, Request, Ack

* which of the following windows command prompt commands will cause a PC to broadcast a DHCP Discover message?
	* `ipconfig /renew`
		* this command causes your PC to look for any DHCP servers it can reach

* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.13.png]]
	* d)
		* we know this from looking at the `Bootp flag` and the `Broadcast flag`
		* because we are broadcasting flags, the destination is 255.255.255.255

* Which of the following messages can be sent unicast?
	* DHCP Ack, DHCIP Release, DHCP Offer

![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.14.png]]

* A)
	* all the other answers don't require the router to be a DHCP relay agent

![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.15.png]]

* F)
	* you want to run configuration on the router closest to the PCs wanting DHCP access using the address of the DHCP server
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.16.png]]
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.17.png]]
	* ![[./_resources/Day_39_-_Dynamic_Host_Configuration_Protocol_(DHCP).resources/image.18.png]]
