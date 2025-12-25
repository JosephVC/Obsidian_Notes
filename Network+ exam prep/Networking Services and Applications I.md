---
---
**The basics of a VPN (Virtual Private Network)**

* **![[./_resources/Networking_Services_and_Applications_I.resources/unknown_filename.png]]**
* A VPN is used by remote hosts to **access a private network** via an encrypted tunnel which goes **through a public network**
* once a VPN connection is made, a remote host is no longer considered remote
	* the host is seen by the network as a local network
	* the connection is seen as local regardless of the other routers or systems passed through
* the use of a VPN can reduce network costs for orgs partly because the VPN doesn't require a dedicated leased line to create a direct connection
* **Types of VPNs**
	*  **site-to-site VPNs**
		* allow a remote site's network to be connected to the main site's network and be seen as a local network segment
			* VPN concentrators on both ends of the VPN will manage the connection
		* **remote access VPN (host-to-site VPN)**
			* allows select remote users to connect to the local network
				* a **VPN concentrator** on the local network will manage the connections coming in from the local users
				* the remote system making the connection uses special software - **VPN client software** - to make a connection
		* **host-to-host VPN (SSL VPN)**
			* allows a secure connection between two systems without the use of VPN client software
				* a **VPN concentrator** on the local network manages the connections
				* the host seeking to connect using a browser that supports either SSL or TLS to make the connection with the VPN concentrator

**Protocols used by VPNs**

* **Internet Protocol Security (IPsec)**
	* a whole suite of protocols
	*  works at layer 3 of the OSI Model
	* the most common suite of protocols to secure a VPN
	* can be used with the **Authentication Header (AH)** protocol
		* only offers authentication, no encryption
	* can be used with **Encapsulated Security Payload (ESP)**
		* this is the most popular protocol, as it both authenticates and encrypts
	* both AH and ESP in one of two modes
		* they can be used in **transport mode** between two endpoints (such as host-to-host VPN)
		* can be used in **tunnel mode** between two endpoints (such as site-to-site VPN)
	*  IPSec implements **Internet Security Association and Key Management (ISAKMP)**
		* this provides a method for transferring security keys and authentication between systems, outside the security key generating process ( this is a much more secure process)
* **Generic Routing Encapsulation (GRE)**
	* tunelling protocol capable of encapsulating a variety of network layer protocols
	* often used to create a sub-tunnell in an IPsec connection
		* IPSec will only transmit unicast packets (one-to-one communications). 
		* There is often a need to transmit multicast (one-to-some) or broadcast (one-to-many) packtes accross an IPsec connection; GRE allows this 
* **Point-to-Point Tunnelling Protocol (PPTP)**
	* supports older dial-up VPN connections
	* lacks  native security features
	* Microsoft implemented this but added GRE
* **Transport Layer Security (TLS) Protocol**
	* cryptographic protocol used to create a secure encrypted connection between two network endpoints or devices
	* uses asymetrical cryptography to authenticate end points, then negotiates a symmetrical security key to encrypt the session
	* largely replaced by the **Secure Socket Layer (SSL)** 
* **Secure Socket Layer (SSL) Protocol**
	* older cryptographic tech similar to TLS
	* most common use is internet transactions
	* all modern web browsers support SSL
	* due to weaknesses of earlier versions of the protocol - corrrected by SSL 3.3, it has largely been replaced by TLS
