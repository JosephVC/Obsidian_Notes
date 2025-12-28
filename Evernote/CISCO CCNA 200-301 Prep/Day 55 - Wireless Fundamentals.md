---
---
**Wireless Networks**

* we focus on LANs over WiFi
* the standards for wireless LANs is IEEE 802.11
* the term **wi-fi** is a term of the **wifi alliance**, but not connected to the IEEE
	* the wifi Alliance tests and certifies equipment for 802.11 standards compliance and interoperability for with other devices
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.png]]
* Wireless networks have some issues that we need to deal with
	* all devices within range receive all frames, similar to devices connected on Ethernet
	* like an ethernet hub, when a wireless device transmits a frame all connected devices can recieve it
		* this means privacy via wifi can be a concern
	* **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)** is used to facilitate half-duplex communications
	* **CSMA/CD** is  used in networks to detect and recover from collisions
	* **CSMA/CA** is used in wireless networks to avoid collisions
	* when using **CSMA/CA**, devices will wait for others to stop transmitting before transmitting data themselves
		* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.1.png]]
* wireless communications are regulated by national and international bodies
* wireless signal coverage area must be considered
	* signal range
	* signal **absorption , reflection, diffraction, scattering**
		* **absorption -** when a wireless signal passes through a material and is converted into heat, weakening the original signal
		* **reflection -** when a signal bounces off a material
			* poor reception in an elevator is an example of this - the signal bounces off metal and little of it gets into the elevator
		* **refraction -** when a wave is bent when entering a medium where the signal travels at a different speed
			* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.2.png]]
		* **diffraction -** happens when encounters and obstacle and travels around it
			* this can result in blind spots around obstacles
			* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.3.png]]
		* other devices on the same channel can cause **interference**

**Radio Frequency**

* to send wireless signals, the sender applies an alternating current to an antenna
	* this creates electromagnetic waves which propagate out as waves
* electromagnetic waves can be measured in multiple ways - **amplitude** and **frequency**
	* **amplitude -** the max strength of the electric and magnetic fields
		* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.4.png]]
	* **Frequency** \- measures the up/down cycles per a given unit of time
		* the most common measurement of frequency is **hertz**
		* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.5.png]]
		* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.6.png]]
	* another important term is **period**, the amount of time per cycle
		* if the frequency is 4 hrz, the period is .25 seconds
* the visible frequency is from approx. 400Thz to 790 THz
* the radio frequency range is from 30 Hz to 300 GHz
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.7.png]]

**Radio Frequency Bands**

* wi-fi uses two main **bands (frequency ranges)**
* 2.4 GHz bands
	* the actual range is **2.400 GHz - 2.4835 GHz**
	* provides more reach in open space and better penetration of obstacles like walls
	* interference can be a bigger issue with 2.4GHz as many devices use it
* 
* 5 GHz band
	* the actual range is from **5.150 GHz - 5.825 GHz**
* **Wi-Fi 6 (802.11ax)** has expanded the spectrum range to include a band in the 6 GHz range

**Channels**

* each band is divided up into multiple channels
	* devices  are configured to transmit and receive traffic on one (or more) of these channels
* 2.4 GHz band is divided into several channels, each on with a 22 MHz range
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.8.png]]
* in a small wireless LAN with only  a single AP, you can use any channel
* however  in larger WLANS with multiple APs, it's important that adjacent APs don't use overlapping channels; this helps avoid interference
	* the 802.11b standard for Japan is and old and slow standard
* **note how all these channels overlap, so carefully choose which frequency access points use**
* in a small wireless LAN is only a single AP, you can use any channel
* in larger WLANs with multiple AP (access points) it is important that adjacent APs don't use overlapping channels; this helps avoid interference
* in the **2.4 GHz band**, it is recommended to use **channels 1, 6, and 11**
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.9.png]]
* while outside of North America you can use other combinations, but for the CCNA remember 1, 6, and 11
* it is easier to avoid interference between adjacent APs using the 5 GHz band, as it consists of non-overlapping channels
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.10.png]]

**802.11 Standards**

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.11.png]]
	* these data rates are largely theoretical, as many things can influence what a user actually receives
	* memorize these standards and their characteristics

**Service Sets**

* 802.11 defines different kinds of **service sets** - **groups of wireless networks**
* **three main types of service sets**
	* **independent**
	* **infrastructure**
	* **mesh**
* all devices in a service set share the same **SSID (Service Set IDentifier)**
	* the SSID is a human-readable name which identifies the service set
	* the SSID **does not have to be unique**
	* **the name you give to your home wifi is an example of an SSID**

**Service Sets: IBSS**

* **IBSS (Independent Basic Service Set) -** a wireless network with two or more wireless devices connect directly without using an **AP (Access Point)**
* also called **ad hoc** networks
* can be used for file transfer, such as AirDrop
* not scalable beyond a few devices
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.12.png]]

**Service Sets:  BSS**

* **BSS (Basic Service Set)** - kind of infrastructure service set in which clients connect to each other via an **AP (Access Point)** but not directly to each other
	* the AP serves as the infrastructure connecting different wireless clients together
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.13.png]]
	
* a **BSSID (Basic Service Set ID)** is used to uniquely identify the AP
	* other APs can use the same SSID but not the same BSSID
	* the BSSID is the MAC address of the APs radio
* to be part of the BSS, wireless devices must request to **associate with** the BSS
* Wireless devices that have associated with the BSS are called **clients** or **stations**
* The area around an AP where its signal is usable is called a **BSA (Basic Service Area)**
* **What is the difference a BSS and BSA**
	* a BSS are a group of devices wirelessly connected around an AP
	* a BSA is the area around the AP where devices can associate with the AP
* clients must communicate via the AP, not directly with each other
	* traffic must flow through the AP before flowing to a client, even if the other client is in range of the AP

**Service Sets: ESS**

* to create larger wireless LANs beyond the range of a single AP, we use an **ESS (Extended Service Set)**
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.14.png]]
* APs with their own BSSs are connected by a wired network
	* each BSS uses the same SSID
	* each BSS has a unique BSSID
	* each BSS has a different channel to avoid interference
* Clients can pass between APs without having to reconnect, providing a seamless Wi-Fi experience when moving between APs
	* the above is called **roaming**
* **BSA's should overlap 10-15%**

**Service Sets: MBSS**

* as **MBSS (Mesh Basic Service Set)** can be used in situations where it's difficult to run an Ethernet connection to every AP
* Mesh APs use two radios: one to provide a BSS to wireless clients, and one to form a **backhaul network** which is used to bridge traffic from AP to AP
* at least one AP is connected to the wired network, and it is called the **RAP (Root Access Point)**
* the other APs are called **MAPs(Mesh Access Points)**
* a protocol is used to determine the best path through the mesh (similar to how dynamic routing protocols are used to determine the best path to a destination)
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.15.png]]

**Distribution System**

* most wireless networks aren't standalone networks
	* rather they act as a way for wireless clients to connect to the wired network infrastructure
* 802.11 the upstream wired network is called the **DS (Distribution System)**
* Each wireless BSS or ESS is mapped to a VLAN in the wired network
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.16.png]]
* It's possible for an AP to provide multiple wireless LANs, each with a unique SSID
* each WLAN is mapped to a separate VLAN and connected to the wired network via a trunk
* each WLAN uses a unique BSSID, usually by incrementing the last digit of the BSSID by one

**Additional AP Operational Modes**

* APs can operate in additional modes beyond the ones we've introduced so far
* an AP in **repeater mode** can be used to extend the range of a BSS
	* the repeater will simply retransmit any signal it receives from the AP
	* a repeater with a single radio must operate on the same channel as the AP, but  this can drastically reduce the overall throughput on the channel
	* a repeater with two radios can receive on one channel, then retransmit on another channel
* a **workgroup bridge (WGB)** operates as a wireless client of another AP, and can be used to connect wired devices to the wireless network
	* below, PC1 does not have wireless capabilities nor can access SW1 via a wired connection
	* PC1 has a wired connection to the WGB, which has a wireless connection to the AP
	* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.17.png]]
	* an **outdoor bridge** can be used to connect networks over long distances without a physical cable connecting them
	* APs use specialized antennas that focus most of the signal power in one direction, thus allowing a wireless connection to be made over longer distances than normally possible
	* below, the connection can be point-to-point or **multipoint**, where multiple sites connect to one central site
	* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.18.png]]

**QUIZ**

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.19.png]]
	* b

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.20.png]]
	* a
		* in 802.11, the wired network is called the **DS (Distribution System)**, and the AP's main role is to connect the wireless system to the main network

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.21.png]]
	* a, d

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.22.png]]
	* b, c

* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.23.png]]
* b 

![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.24.png]]

* E
* ![[./_resources/Day_55_-_Wireless_Fundamentals.resources/image.25.png]]
