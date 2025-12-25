---
---
**Network Access Services**

* **Network Interface Controller (NIC)**
	* can also be called a **Network Interface Card**
	* the NIC is how a device connects to a network
	* works at 2 different layers of the OSI model 
		* at **layer 2** (data link layer) provides the functional means of network communication by determining which networking protocols will be used provides the local network node address via its burned-in MAC address
		* at **layer 1** (physical layer), it determines how the network data traffic will be converted a bit at a time into an electrical signal that can traverse the network media being used
	* most modern computers come with at least one built-in ethernet NIC
	* devices like routers may use separate modules which can be swapped out to provide the proper NIC for the type of media they are connecting to and the protocol being used
* **RADIUS (Remote Authentication Dial In User Service)**
	* a remote access service that is used to authenticate remote users and grant them access to authorized network resources
	* popular **AAA (Authentication, Authorization, and Accounting)** protocol to ensure that end users are using the proper network resources they are authorized to use
	* only the requestor's (the end user's) password is encrypted
* **TACACS+ (Terminal Access Controller Access-Control System Plus)**
	* a remote access service that is used to authenticate remote devices and grant them access to authorized network resources
	* popular AAA protocol used to help ensure that only authenticated remote network devices are using the appropriate network resources
		* less robust than RADIUS
	* all transmissions between devices are encrypted

**Other Services and Applications**

* **RAS (Remote Access Services)**
	* not a protocol, but a roadmap
	* a description of the combination of hardware and software required for a remote access connection
	* a client requests access from a RAS server, which either grants or rejects access
* **Web Services**
	* create a means of cross communication
	* will translate communication into XML or JSON (when communicating with APIs)
* **Unified Voice Services**
	* creates better voice communication services
	* combination of software and hardware needed to integrate voice communication into a network
