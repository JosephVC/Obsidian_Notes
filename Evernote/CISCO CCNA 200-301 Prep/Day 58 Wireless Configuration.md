---
---
**Network Topology**
![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.png]]

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.1.png]]

**Suppose a computer wants to communicate with its default gateway via the internal WVLAN**

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.2.png]]

**Suppose a computer on the internal WVLAN wants to use the guest network to communicate with its default gateway**

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.4.png]]

**1st half of the above configuration**
![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.5.png]]

**2nd half of configuration**
![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.3.png]]

**WLC Initial Setup**

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.6.png]]

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.8.png]]

![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.9.png]]

**Take care that the country code on  your device matches up with the regulatory domain of the AP**
![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.7.png]]

**Accessing the GUI**

* accessing WLCs IP address in a web browser to access it's GUI
* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.10.png]]
* enter the admin credentials set up earlier
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.11.png]]
* now you see the dashboard
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.13.png]]
		* note there are two green interfaces (up) and two red (down)
		* the green interfaces are forming a LAG
* from within the **Controller tab** at the top, we then go to **Interfaces** 
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.12.png]]
	* these are not physical ports but logical/virtual ones; **ports** and **interfaces** can be used interchangeably 
	* in the context of **WLCs**, **port = physical port** and **interface = logical interface**
* now click on the **New** button highlighed above, then apply the new interface
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.17.png]]

* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.16.png]]
* Now we see that the new interface called **internal** has been created
* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.15.png]]
* Now we go to create our **guest** interface
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.18.png]]
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.20.png]]
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.19.png]]
* **Configuring the WLANs**
	* we start by going into the WLAN tab
		* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.21.png]]
		* we need to alter the **security policy**, as it uses 802.X authentication; **for the CCNA we need to configure pre-shared key authentication (WPA personal mode)**
			
			* we need to click on the WLAN ID to change the above
			* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.23.png]]
			* Select the 'internal interface' from the **Interface/Interface Group (G)** menu
			* then select the **Security** tab
				* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.22.png]]
					* the highlighted sections are what we should have for the CCNA
				* We now need to look at the **Authentication Key Management** section
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.25.png]]
					* make sure the password set for PSK is long enough
						* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.24.png]]
				* if you happen to configure the **Layer 3** tab, you may get options for 'web policy'
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.26.png]]
					* **Web Authentication:**  after the wireless clients get an IP address and tries to access a web page, they will have to enter a username and password to authenticate
					* **Web Passthrough:** Similar to the above, but no username or password is required.  A warning or statement is displayed and the client simply has to agree to gain access to the Internet
					* the **conditional** and **splash page** we redirects options are similar, but additionally require 803.1X layer 2 authentication
			* now we set up the QoS tab
				* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.28.png]]
				* the exam requires that all the above QoS settings be understood
			* we don't need to consider the settings in the Advanced tab
				* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.27.png]]
			* then we have to set up the WLANs
				* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.29.png]]
					* the **profile name** is meant to set up the WLAN in the WLC
				* two things need to be changed when we set up the WLAN
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.30.png]]
					* **to the below**
						* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.31.png]]
			
			* now we return to the monitoring dashboard
				* we need to change the **clients associated with the APs**
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.32.png]]
					* **after joining with our own wireless devices, there are now three clients**
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.34.png]]
					* **you can also click on the "Clients" link on the left side of the menu**
					* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.35.png]]

* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.33.png]]

**WLC Ports/Interfaces**

* WLC **ports** are the physical ports that cables connect to
* WLC **interfaces** are the logical interfaces within the WLC (ie. SVIs on a switch)
* WLCs have a few different **ports**
	* **Service Port:** dedicated management port.  Used for out-of-band management.  Must connect to a switch access port because it only supports on VLAN.  This port can be used to connect to the device while it is booting, perform system recovery, etc.
	* **Distribution system port:** These are the standard network ports that connect to the distribution system (wired network) and are used for data traffic.  These ports usually connect to switch trunk ports, and if multiple distribution ports are sued they can form a LAG
	* **Console port:** this is a standard console port, either RJ45 or USB
	* **Redundancy port:** this port is used to connect to another WLC to form a **higher availability (HA)** pair
	* ![[./_resources/Day_58_Wireless_Configuration.resources/unknown_filename.14.png]]
* WLCs have a variety of **interfaces** as well
	* **Management interface:** Used for management traffic such as Telnet, SSH, HTTP, HTTPS, RADIUS authentication, NTP, Syslog, etc.  CAPWAP tunnels are also formed to/from the WLC's management interface
	* **Redundancy management interface:** when two WLCs are connected by their redundancy ports, one WLC is 'active' and another is on 'standby'.  This interface can be used to connect to and manage the 'standby' WLC
	* **Virtual interface:** this interface is used when communicating with wireless clients to relay DHCP requests, perform client web authentication, etc.
	* **service port interface:** if the service port is used, this interface is bound to it and used for out-of-band management
	* **dynamic interface:** these are the interfaces used to map a WLAN to a VLAN.  as an example, traffic from the 'Internal' WLAN will be sent to the wired network from the WLC's 'internal' dynamic interface

**WLC Configuration**

1. ![[./_resources/Day_58_Wireless_Configuration.resources/image.png]]

* then hit Apply
	

2. 
![[./_resources/Day_58_Wireless_Configuration.resources/image.1.png]]

3. ![[./_resources/Day_58_Wireless_Configuration.resources/image.1.png]]
4. ![[./_resources/Day_58_Wireless_Configuration.resources/image.2.png]]
5. ![[./_resources/Day_58_Wireless_Configuration.resources/image.3.png]]
6. ![[./_resources/Day_58_Wireless_Configuration.resources/image.4.png]]
7. ![[./_resources/Day_58_Wireless_Configuration.resources/image.5.png]]
8. ![[./_resources/Day_58_Wireless_Configuration.resources/image.6.png]]
9. ![[./_resources/Day_58_Wireless_Configuration.resources/image.7.png]]
10. ![[./_resources/Day_58_Wireless_Configuration.resources/image.8.png]]
11. ![[./_resources/Day_58_Wireless_Configuration.resources/image.9.png]]
12. ![[./_resources/Day_58_Wireless_Configuration.resources/image.10.png]]
	* **web authentication:**  after the wireless clients get an IP address and tries to access a web page, they will have to enter a username and password to authenticate
	* **web passthrough:**  similar to the above, but with no username and password being required; a warning or statement is displayed and the client simply has to agree to gain access to the internet
	* the **conditional** and **splash page** web redirect options are similar, but additionally require 802.1X layer 2 authentication

13. 
![[./_resources/Day_58_Wireless_Configuration.resources/image.11.png]]

14. ![[./_resources/Day_58_Wireless_Configuration.resources/image.12.png]]
15. ![[./_resources/Day_58_Wireless_Configuration.resources/image.13.png]]
16. ![[./_resources/Day_58_Wireless_Configuration.resources/image.14.png]]
17. ![[./_resources/Day_58_Wireless_Configuration.resources/image.15.png]]

![[./_resources/Day_58_Wireless_Configuration.resources/image.16.png]]

![[./_resources/Day_58_Wireless_Configuration.resources/image.17.png]]

**QUIZ**

1. ![[./_resources/Day_58_Wireless_Configuration.resources/image.18.png]]
	* b

2. ![[./_resources/Day_58_Wireless_Configuration.resources/image.19.png]]

* A

3. ![[./_resources/Day_58_Wireless_Configuration.resources/image.20.png]]

* D

4. ![[./_resources/Day_58_Wireless_Configuration.resources/image.21.png]]

* B
* ![[./_resources/Day_58_Wireless_Configuration.resources/image.22.png]]

5. ![[./_resources/Day_58_Wireless_Configuration.resources/image.23.png]]

* **B**

![[./_resources/Day_58_Wireless_Configuration.resources/image.24.png]]

* D
* ![[./_resources/Day_58_Wireless_Configuration.resources/image.25.png]]
* ![[./_resources/Day_58_Wireless_Configuration.resources/image.26.png]]
