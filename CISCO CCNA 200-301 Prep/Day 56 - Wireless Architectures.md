---
---
**802.11 Frame Format**

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/image.png]]
* 802.11 frames have a different format than 802.3 Ethernet frames
* depending on the 802.11 version and message type, some of the fields might not be present in the frame
	* **while there are 4 different address fields,  not all messages use them all**
* **frame control:** provides information such as the message type and subtype
* **duration/ID:** depending on the message type, this field can indicate
	* the time (in microseconds) the channel will be dedicated for transmission of the frame
	* the identifier for the association (connection)
* **Addresses:** up to four addresses can be present in an 802.11 frame; which addresses are present, and their order, depends on message type
	* **destination address (DA):** final recipient of the frame
	* **Source address (SA):** original sender of the frame
	* **Receiver Address (RA):** Immediate recipient of the frame
	* **Transmitter Address (TA):** immediate sender of the frame
* **Sequence Control:** used to reassemble fragments and eliminate duplicate frames
* **QoS Control:** Used in QoS to prioritize certain traffic
* **HT (High Throughput) Control:** Added in 802.11n to enable to enable High Throughput operations
	* 802.11n is also known as **High Throughput (HT) Wi-Fi**
	* 802.11ac is also known as **Very High Throughput (VHT) Wi-Fi**
* **Frame Body:** the actual data packet being sent
* **FCS (Frame Check Sequence):** same as in Ethernet frame, used to check for errors

**802.11 Association Process**
![[./_resources/Day_56_-_Wireless_Architectures.resources/image.1.png]]

* Access points bridge traffic between wireless stations and other devices
* for a station to send traffic through the AP, it must be associated with the AP
* there are three 802.11 connection states
	* not authenticated, not associated
	* authenticated, not associated
	* authenticated and associated
* the station must be authenticated and associated with the AP to send traffic through it
	1. a station sends a **probe request** to learn what APs and DSSs are available
	2. the AP sends a **probe response** back
		* there are two ways a station can scan for a BSS
			* **active scanning:** the station sends probe requests and listens for a probe response from an AP
			* **passive scanning:** the station listens for a **beacon** message from the AP; beacon messages are sent periodically by APs to advertise the BSS
			* **we are still not authenticated, not associated**
	3. there is the **authentication request** and **authentication response**
		* this brings us to the stage of being **authenticated, not yet associated**

4. finally, there is the **association request** and **association response**

* if this is successful, we  have the final state of **authenticated and associated**

* **all of the above messages are of the same type**

**802.11 Message Types**

* **Management:** used to manage the BSS
	* Beacon
	* Probe request, probe response
	* Authentication
	* Association request, association response
* **Control:** used to control access to the medium (radio frequency).  Assists with delivery of management and data frames
	* RTS (Request to Send)
	* CTS (Clear to Send)
	* ACK
* **Data:** used to send actual packets

![[./_resources/Day_56_-_Wireless_Architectures.resources/image.2.png]]
**Autonomous APs**

* there are three main wireless AP deployment methods: autonomous, lightweight, and cloud-based
* **Autonomous**
	* self-contained systems that don't rely on a WLC
	* are configured individually
		* can be configured by console cable (CLI), telnet/SSH (CLI), or HTTP/HTTPS web connection (GUI)
		* an IP address for remote management should be configured
		* the RF parameters must be manually configured (transmit power, channel, etc.)
		* security policies are handled individually by each AP
		* QoS rules, etc. are configured individually on each AP
	* there is no central monitoring or management of APs
	* Autonomous APs connect to the wired network with a trunk link
		* even if there is only one SSID, the connection should be to a trunk
			* because the management traffic used to remotely connect to the wireless APs, along with other devices such as switches, should be in a separate VLAN
				* it's best to keep management traffic separate from regular data traffic by putting it in a separate VLAN and subnets
	* Data traffic from wireless clients has a very direct path to the wired network or to other wireless clients associated with the same AP
		* ![[./_resources/Day_56_-_Wireless_Architectures.resources/image.3.png]]
	* Each VLAN has to stretch across the entire network; this is considered bad practice
		* creates large broadcast domains
			* each VLAN is considered a broadcast domain, and if these VLANs are stretched across a whole network each broadcast message will be flooded a throughout the whole domain
		* spanning tree will disable links
			* modern networks want to avoid spanning tree as much as possible, as disabling links will reduce total bandwidth
		* adding/deleting VLANs is very labor-intensive
	* autonomous APs can be used in small networks but they are not viable in medium to large networks
		* a large network can have thousands of APs, and managing them individually is not feasible
	* autonomous APs can also function in the modes covered in the previous video: repeater, outdoor bridge, workgroup bridge

**Lightweight APs**

* the functions of an AP can be split between the AP and a **Wireless LAN Controller (WLC)**
* **Lightweight APs** handle **real-time operations** like transmitting/receiving RF traffic, encryption/decryption of traffic, sending out beacons/probes, etc.
* other functions are carried out by a WLC, such as RF management, security/QoS management, client authentication, client association/roaming management, etc.
* This is called **split-MAC architecture**
* the WLC is also used to centrally configure the lightweight APs
* the WLC can be located in the same subnet/VLAN as the lightweight APs it manages, or in a different subnet/VLAN
* the WLC and the lightweight APs authenticate each other using digital certificates installed on each device (X.509 standard certificates)
	* this ensures only authorized APs can access the network
* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.png]]
	* the WLC and lightweight APs use a protocol called **CAPWAP (Control And Provisioning of Wireless Access Points)** to communicate
		* Based on an older protocol called **LWAPP (Lightweight Access Point Protocol)** 
	* Two tunnels are created between each AP and WLC
		* Control tunnel (UDP port 5246).  This tunnel is used to configure the APs, and control/manage the operations.  All traffic in this tunnel is encrypted by default
		* Data tunnel (UDP port 5247). All traffic from wireless clients is sent through this tunnel to the WLC.  **It does not go directly to the wired network**
		* Traffic in this tunnel is not encrypted by default, but you can configure it to be encrypted with the **DTLS (Datagram Transport Layer Security)**
		* Because all traffic from wireless clients is tunneled to the WLC with CAPWAP, APs connect to switch access ports, not trunk ports
		* there are some **key benefits** to split-MAC architecture, here are a few
			* **scalability -** with a WLC (or multiple or very large networks), its much simpler to build and support a network with thousands of APs
			* **dynamic channel assignment** - the WLC can automatically select which channel each AP should use
			* **Transmit power optimization -** the WLC can automatically set the appropriate transmit power for each AP
			* **self-healing wireless coverage -** when an AP stops functioning, the WLC can increase the transmit power of nearby APs to avoid coverage holes
			* **seamless roaming -** clients can roam between APs with no noticeable delay
			* **client load balancing -** if a client is in range of two APs, the WLC can associate the client with the least-used AP, to balance the load among APs
			* **Security/QoS management -** Central management of security and QoS policies ensures consistency across the network
			* Lightweight APs can be configured to operate in various modes
				* **Local -** this is the default mode where the AP offers a BSS (more multiple BSSs) for clients to associate with
				* **FlexConnect -** like a lightweight AP in Local mode, it offers one or more BSSs for clients to associate with.  However, FlexConnect allows the AP to locally switch traffic between the wired and wireless networks if the tunnels to the WLC go down
					*  ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.2.png]]
				* **Sniffer -** the AP does not offer a BSS for clients; it is dedicated to capturing 802.11 frames and sending them to a device running software such as WireShark
				* **Monitor -** the AP does not offer a BSS for clients.  it is dedicated to receiving 802.11 frames to detect rogue devices.  if a client is found to be a rogue device, the AP can send de-authentication messages to disassociate the rogue device from the AP
				* **Rogue Detector -** the AP does not even use its radio.  It listens to traffic on the wired network only, but is receives a list of suspected rogue clients and AP MAC addresses from the WLC;  by correlating the received ARP messages it listens for on the wired network and the information received from WLC, it can detect rogue devices
				* **SE-Connect (Spectrum Expert Connect -** the AP does not offer a BSS for clients.  It is dedicated to RF spectrum analysis on all channels.  It can send information to software such as Cisco Spectrum Expert on a PC to collect an analyze data
				* **Bridge/Mesh -** like the autonomous APs **outdoor bridge** mode, the lightweight AP can be a dedicated bridge between sites, such as over long distances.  a mesh can be made between the access points
					* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.3.png]]
				* **Flex plus Bridge -** Adds FlexConnect functionality to the Bridge/Mesh mode. . Allows wireless access points to locally forward traffic even if connectivity to the WLC is lost
				* **the above list does not need to be memorized, but just understand the basics of each mode**

![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.1.png]]

**Cloud-based AP**

* cloud based AP architecture is in between autonomous AP and split-MAC architecture
	* Autonomous APs that are centrally managed in the cloud
		
* Cisco Meraki is a popular cloud-based Wi-Fi solution
	* **for the CCNA, be aware of Meraki**
	* the Meraki dashboard can be used to configure APs, monitor the network, generate performance reports, etc.
		* Meraki also tells each AP which channel to use, what transmit power, etc.
* However, data traffic is not sent to the cloud.  It is sent direclty to the wired network like when using autonomous APs
	* Only management/control traffic is sent to the cloud
* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.4.png]]
* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.5.png]]

**WLC Deployment Models**

* in a split-MAC architecture, there are four main WLC deployment models
	* **Unified -** the WLC is a hardware appliance in a central location on the network
		* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.6.png]]
		* suitable for a large campus
		* can support up to 6000 APs
		* if more than 6000 APs are needed, additional WLCs can be added to the network
	* **cloud-based -** the WLC is a VM running on a server, usually in a private cloud in a data center; **this is not the same as the cloud-based AP architecture discussed previously**
		* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.7.png]]
		* cloud-based WLCs can typically support up to 3000 APs
		* more WLC VMs can be deployed if needing more than 3000 APs
	* **embedded -** the WLC is integrated within a switch
		* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.9.png]]
		* embedded WLCs can support up to 200 APs
		* if more than 200 APs are needed, more switches with embedded WLCs can be added
	* **mobility express -** the WLC is integrated within an AP
		* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.10.png]]
		* a Mobility Express WLC can support up to about 100 APs
		* if more than 100 APs are needed, you'll need to add more APs with Mobility Express included
		* good for small offices

**QUIZ**

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.8.png]]
	* c
	* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.11.png]]

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.12.png]]
	* C, D
	* lightweight AP are centrally managed by a wireless LAN controller, while cloud-based AP are centrally managed by a cloud server

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.13.png]]
	* C
	* CAPWAP is  used to communicate to the WLC via two tunnels - a control and a data tunnel

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.14.png]]
	* A, C

* ![[./_resources/Day_56_-_Wireless_Architectures.resources/unknown_filename.15.png]]
	* D
