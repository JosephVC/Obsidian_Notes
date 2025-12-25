---
---
* Understanding Syslog is essential for system admins
* Syslog is an industry standard protocol for message logging
* on network devices, syslog can be used to log events such as changes in interface status (up/down), changes in OSPF neighbor status (up/down), system restarts, etc.
* the messages can be displayed in the CLI, saved in the device's RAM, or sent to an external syslog server
* the output in the orange box are syslog messages concerning network changes
	* ![[./_resources/Day_41_-_Syslog.resources/image.png]]
* logs are essential when troubleshooting issues, examining the cause of incidents, etc.
* syslogs and SNMP are both used for monitoring and troubleshooting devices; they are complimentary but functionally different

**Syslog message format**

* ![[./_resources/Day_41_-_Syslog.resources/image.1.png]]

**Syslog severity levels**

* **syslog messages severity 0 to 6 are saved to the logging buffer**
* ![[./_resources/Day_41_-_Syslog.resources/image.2.png]]
	* because severities are subjective, do not assume that all equipment have the same definition of severity - **The Syslog Protocol**
	* ![[./_resources/Day_41_-_Syslog.resources/image.3.png]]
		

**Syslog Message Examples**

* ![[./_resources/Day_41_-_Syslog.resources/image.4.png]]
	

**Syslog Logging Locations**

* **Console line -** syslog messages will be displayed in the CLI when connected to the device via the console port; by default, all messages (lvl 0-7) will be displayed
* **VTY lines** - messages will be displayed in the CLI when connected to the device via **Telnet/SSH**; disabled by default
* **Buffer** - syslog messages will be saved to RAM; by default all messages (lvl 0-7) are displayed
	* you can view the messages with the `show logging` command
* **External server -** you can configure the device to send syslog messages to an external server
	* **Syslog servers will listen for messages on UDP port 514**

**Syslog Configuration**

* ![[./_resources/Day_41_-_Syslog.resources/image.5.png]]

**terminal monitor**

* even if the `logging monitor` **level** is enabled, by default syslog messages will not be displayed when connected via Telnet or SSH
* for the messages to be displayed, you must use the following command `terminal monitor`
	* this command must be used **every time you connect to the device via Telnet or SSH**

**logging synchronous**

* by default, logging messages displayed in the CLI while you are in the middle of typing a command will result in something like this
	* ![[./_resources/Day_41_-_Syslog.resources/image.6.png]]
* to prevent this, you should use the **logging synchronous** on the appropriate **line**
	* ![[./_resources/Day_41_-_Syslog.resources/image.7.png]]
* this will cause a new line to be printed if your typing is interrupted by a message
	* ![[./_resources/Day_41_-_Syslog.resources/image.8.png]]

**service timestamps/service sequence-numbers**

* ![[./_resources/Day_41_-_Syslog.resources/image.9.png]]

**Syslog Command Summary**

* ![[./_resources/Day_41_-_Syslog.resources/image.10.png]]

**Syslog v. SNMP**

* syslog and SNMP are both used for monitoring and troubleshooting of devices; they are complementary, but their functionalities are different
* **syslog** is used for message logging
	* events within the system are categorized based on their severity/facility and then logged
	* used for system management, analysis and troubleshooting
	* messages are sent from the devices to the server; the server **can't** actively pull information from the devices (like SNMP **get**) or modify variables (like SNMP **set**)
* **SNMP** is used to retrieve and organize information about the SNMP managed devices
	* IP addresses, current interface status, temperature, CPU usage, etc.
	* SNMP servers can use **get** to query the clients and **set** to modify variables on the clients

**QUIZ**

* ![[./_resources/Day_41_-_Syslog.resources/image.11.png]]
	* severity is a **Notice/Notification**

* ![[./_resources/Day_41_-_Syslog.resources/image.12.png]]
	* severity is **Error**

* ![[./_resources/Day_41_-_Syslog.resources/image.13.png]]
	* Console line, buffer
		* syslog will only send logs to an external server once you configure it

* ![[./_resources/Day_41_-_Syslog.resources/image.14.png]]
	* severity 0 to 6

* ![[./_resources/Day_41_-_Syslog.resources/image.15.png]]
	* **seq, time stamp**
