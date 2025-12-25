---
---
**WAN Architecture**

* WAN = Wide Area Network
	* a network that extends over a large geographic network
	* used to connect geographically separate LANs
	* although the Internet itself can be considered a WAN, the term is used to refer to an enterprise's private connections that connect offices, data centers, and other sites
	* VPNs can be used to create private WAN connections
	* there have been many WAN technologies over the years and their availability depends on on location
	* technology considered legacy in one area may be still used in others

**WAN over dedicated connection (leased line)**

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.png]]

**WAN over shared infrastructure (Internet VPN)**

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.1.png]]

**Leased Line**

* leased lines are physical links, typically connecting two sites
* leased lines use serial connections (PPP or HDLC encapsulation)
* there are various standards to provide different speeds, and each country may have its own standard
* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.2.png]]
* Ethernet WAN technology is becoming more popular given the higher cost, install time, and slower speeds of leased lines

**MPLS**

* MPLS = Multiple Protocol Label Switching
* uses labels to forward traffic, not IP addresses
* Similar to the internet, service providers' MPLS are shared infrastructure because many customer enterprises connect to and share the same infrastructure to make WAN networks
* however, label switching in the  name of MPLS allows VPNs to be created over MPLS infrastructure through the use of labels
* some important terms:
	* **CE router = Customer Edge router - DOES NOT USE MPLS**
	* **PE router = Provider Edge router**
	* **P router = Provider core router**
* When the PE routers receive frames from the CE routers, they add a label to the frame
* these labels are used to make forwarding decisions within the service provider network, _not the destination IP_
* the CE routers do not  use MPLS, it is only used by the PE/P routers
*   when using **layer 3 MPLS VPN**, OSPF peerings are made with PE routers
* in the below, Office A and B's CE will peer with a PE, and thus Office A and B will learn of each other's routes 
* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.3.png]]

* when using **Layer 2 MPLS VPN,** the entire service provider is transparent to the customer
* the service provider is entirely **transparent** to the CE routers
	* **effectively, the two CE routers are directly connected**
	* their WAN interfaces will be in the same subnet
* if a routing protocol is used, two CE routers will peer directly with others
* the CE routers are connected to the PE routers, and the PE network is operating like a big switch
* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.4.png]]

* many different technologies can be used to connect to a service provider's MPLS network for WAN service
* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.5.png]]

**Internet Connectons**

* there a wide range of ways to access the Internet
	* private WAN technologies such as leased lines and MPLS VPNs can be used to connect to a service provider's internet infrastructure
	* CATV/DSL can be used by both consumers and the Enterprise
	* both consumers and businesses can access fiber optic, given their high speeds and long-distance communication

**Digital Subscriber Line (DSL)**

* provides internet connectivity over phone lines, and can share the same phone line that is already installed in most homes
* a DSL modem (modulator/demodulator) is required to convert data into a format suitable to be sent over phone lines
	* the modem might be a separate device or incorporated into a 'home router'

**Cable Internet**

* provides access via the same CATV (Cable television) lines used for TV service
* like DSL, a cable modem is needed to convert data into a suitable format to be sent over the CATV cables; this can be built into the home router

**Redundant Internet Connections**

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.6.png]]

**Internet VPNs**

* private WAN services such as leased lines and MPLS provide security because each customer's traffic is separated by using dedicated physical connections (leased line) or by MPLS tags
* when  using the Internet as  a WAN to connect sites together, there is no built-in security by default
* to provide secure communications over the internet, VPNs are used
* there are two types of VPNs to cover here
	* **site-to-site VPNs using IPsec**
		* a VPN between two devices and is used to connect two sites together over the Internet
		* a VPN tunnel is created between the two devices by encapsulating the original IP packet with a VPN header and a new IP header
			* when IPsec, the original packet is encrypted before being encapsulated with the new header
		* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.7.png]]
		* **summary**
			1. the sending device combines the original packet and session key (encryption key) and runs them through an encryption formula
			2. the sending device encapsulates the encrypted packet with a VPN header and a new IP header
			3. the sending device sends the new packet to the device on the other side of the tunnel
			4. the receiving device decrypts the data to get the original packet, then forwards the original packet to its destination
		* in a site-to-site VPN, a tunnel is formed only between two tunnel endpoints, such as two routers connected to the Internet
		* the other devices on site don't need to create a VPN, but rather can send unencrypted data to their site's router, which will encrypt it and forward it in the tunnel as described above
		* **limitations to standard IPsec**
			* IPsec doesn't support broadcast over multicast traffic, only unicast.  this means that routing protocols such as OSPF can't be used over the tunnels, because they rely on multicast traffic
				* this can be solved with **GRE over IPsec**
					* creates tunnels like IPsec, but does not encrypt traffic
					* does has the advantage of being able to encapsulate a wide variety of Layer 3 protocols as well as broadcast and multicast messages
					* to get the flexibility of GRE with the security of IPsec, **GRE over IPsec** is used
					* (1) the original packet will be encapsulated by a GRE header and a new IP header, and then (2) the GRE packet will be encrypted and encapsulated within an IPsec VPN header and a new IP header
						1. ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.8.png]]
						2. ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.9.png]]
			* Configured a full mesh of tunnels between many sites in a labor-intensive task
				* this can be solved with Cisco's **DMVPN**
					* **DMVPN (Dynamic Multipoint VPN)**  is a Cisco developed solution that allows routers to dynamically create a full mesh of IPsec tunnels without having to manually configure every single tunnel
					* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.10.png]]
	* **remote-access VPNs using TLS**
		* while site-to-site VPNs are used to make an end point-to-point connection between two sites over the Internet, remote-access VPNs are used to allow end devices (PCs, mobile phones) to access the company's internal resources securely over the Internet
		* remote-access VPNs typically use TLS (Transport Layer Security)
			* TLS is also what provides security for HTTPS
			* TLS was formerly known as SSL (Secure Sockets Layer, made by Netscape), but it was renamed to TLS when it was standardized by IETF
		* VPN client software (such as cisco AnyConnect) is installed on end devices
		* these end deices then form secure tunnels to one of the company's routers/firewalls acting as a TLS server
		* the above allow the end users to securely access resources on the company's internal network without being directly connected to the company network
		* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.11.png]]

**Site-to-Site v. Remote Access VPN**

* **site-to-site** **VPNs**
	* typically use IPsec
	* provide service to many devices within the sites they are connecting
	* typically provide service to the one end device the VPN client software is installed on
* **remote-access VPNs**
	* typically use TLS
	* provide service to the one end device the VPN client software is installed on
	* VPNs are typically used to provide on-demand access for end devices that want to securely access company resources while connected to a network which is not secure

**QUIZ**

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.13.png]]

* B

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.12.png]]

* C

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.14.png]]

*  C

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.16.png]]

* B

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.15.png]]

* c

![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.17.png]]

* A
* ![[./_resources/Day_53_-_WAN_Architectures.resources/unknown_filename.18.png]]
