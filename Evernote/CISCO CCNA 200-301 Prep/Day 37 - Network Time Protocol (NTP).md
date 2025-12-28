---
---
**The Importance of Time**

* all devices have an internal clock
* in Cisco IOS, you can view the time with the `show clock`  command
	* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.png]]
		
* using `show clock detail` command, you can see the time source
	* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.1.png]]
* the internal clock of a device will **drift over time**, so it's not the ideal time source
* from the CCNA perspective, **the most important reason to have accurate time on a device is to have accurate logs for troubleshooting**
* **Syslog** the protocol used to keep device logs, will be covered in a later video

**show logging**

* the command to show a device's logs is **show logging**
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.2.png]]
	

**Manual Time Configuration**

* you can manually configure the time on the device with the `clock set` **command**
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.3.png]]
* although the hardware calendar (built-in clock) is the default time-source, the hardware clock and software clock are separate and can be configured separately

**Hardware clock (Calendar) Configuration**

* you can manually configure the hardware clock with the `calendar set` command
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.4.png]]
* typically you will want to synchronize the 'clock' and 'calendar'
* use the command `clock update-calendar` to sync the calendar to the clock's time
	* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.5.png]]
		
* use the command `clock read-calendar` to sync the clock on the calendar's time
* the command `clock timezone` allows configuration of the device's time zone
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.6.png]]

**Network Time Protocol**

* manually configuring the time on devices is no scalable
* the manually configured clocks will drift, resulting in inaccurate time
* **NTP (Network Time Protocol)** allow s automatic syncing of time over a network
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.7.png]]
*   NTP clients request the time from NTP servers
* device can be an NTP server and an NTP client at the same time
* NTP allows accuracy of time within ~1 millisecond if the NTP server is in the same LAN, or within ~50  milliseconds if connecting to the NTP server over a WAN/the internet
* some NTP servers are 'better' than others.  the 'distance' of an NTP server from the original **reference clock** is called **stratum**
* NTP uses UDP port 123 to communicate

**Reference Clocks**

* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.8.png]]
	
* a reference clock is usually a very accurate time device like an atomic clock or a GPS clock
* Reference clocks are **stratum 0** within the NTP hierarchy
* NTP servers directly connected to reference clocks are **stratum 1**

**NTP Hierarchy**

* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.9.png]]
	* the ability for NTP servers to peer with each other is **symmetric active mode**
	* Cisco devices can operate in three NTP modes, or all of them at once
		* Server mode
		* Client mode
		* Symmetric active mode
			
	* **primary servers -** NTP servers which get their time directly from reference clocks
	* **secondary servers -** NTP

**NTP Configuration**

* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.10.png]]
	* it does not matter the order of servers you specify with the `ntp server` command
		* the router will ask all for the time and select the one that gives the quickest response
		* if the current server's responses start slowing down, the router might select another server
	* it's best to supply multiple servers so that the router will have a reliable source of time
	* you can use the `prefer` flag to specify a preferred server, with the other servers as backups
	* `show ntp associations`
		* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.11.png]]
	* `show ntp status`
		* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.12.png]]
	* `do show clock detail` , `do show calendar`
		* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.13.png]]
	* configures the router to update the hardware clock (calendar) with the time learned via NTP
		* you want the **sync the hardware clock** as it tracks the date and time on the device even if it restarts, power is lost, etc.  When the system is restarted, the hardware clock is used to initialized the software clock
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.14.png]]
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.15.png]]

**Configuring NTP Server Mode**

* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.16.png]]
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.17.png]]
	* the highlighted box demonstrates that R1 is using itself as itself as its reference clock
		* the reason is that 127.xxx. type address is reserved for **loopback addresses**
		* loopback addresses/loopback interfaces are different concepts
		* **loopback interfaces** are virtual interfaces in the router, and their address can be advertised to other routers via OSPF
		* **loopback addresses** are completely internal to a device and can't be reached by other addresses
* `show ntp status` will show the stratum level of a device
	* the default stratum of the **ntp master** command is 8

**Configuring NTP symmetric active mode**

* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.18.png]]

**Configuring NTP Authentication**

* NTP authentication can be configured, but it is optional
* it allows NTP clients to ensure they only sync to the intended server
* the configure NTP authentication
	* `npt authenticate` = enables NTP authentication
	* `ntp authentication-key --your key number-- md5 --your key--` = create the NTP authentication key(s)
	* `ntp trusted-key --your key number--` = specify the trusted key(s) 
	* `ntp server -- some ip address-- key --key-number--` = specify which key to use for the server; this command isn't needed on the server
* ![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.19.png]]

**NTP Command Review**
![[./_resources/Day_37_-_Network_Time_Protocol_(NTP).resources/image.20.png]]
