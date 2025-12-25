---
---
**OSI Model**

* **networking models** categorize and provide a structure for networking protocols and standards
	* the **model** will contain a variety of standards, models, and protocols
	* a **networking protocol** is a logical set of rules defining how network devices and software should work
* the **OSI model** stands for **Open Systems Interconnection** model
	* conceptual model that categorizes and standardizes the different functions in a network
	* created by the **International Organization for Standardization (ISO)**
	* divided into 7 layers
	* these layers work together to make the whole network function
	* network engineers usually don't work with the top three layers, but rather **application developers** work with layers 7-5 to connect their applications over networks
		* **layer 7 - Application**
			* layer closest to the end-user
			* interacts with software applications (web browsers, etc.)
			* HTTP and HTTPS are layer 7 protocols
			* identifies communication partners
			* synchronizing communication
			* data interacting with layer 7 will be **encapsulated** as it goes on down through the other layers which may append data; the data is then sent to the layer 1 of another system and is **de-encapsulated** (data is removed) as data moves up layers
				* **adjacent-layer interaction** is when different layers of the OSI model interact with each other
				* ![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/unknown_filename.2.png]]
				* **Same-layer interaction** is where the same layers of systems interact with each other

* **Layer 6 - Presentation**
	* data in the application is the 'application format'
	* data needs to be translated to a different format to be sent over the network
	* the presentation layer's job is to translate between application and network formats
	* an example is the sending of encryption data and decryption of that data when it's received
	* translates between different Application-layer formats
* **Layer 5 - Session**
	* controls dialogs (sessions) between communicating hosts
	* establishes, manages, and terminates connections between local applications (someone's web browser) and the remote application (YouTube)
* **Layer 4 - Transport**
	* after the top three layers deliver data to the bottom four layers, the 4th layers adds a **header** to the data; this data, plus the L4 header, is called a **segment**
	* segments and reassembles data for communications between end hosts
		* breaks large pieced of data into smaller segments which can be more easily sent over the network and are less likely to cause transmission problems if error occurs
			* it is easier to tolerate errors in many small pieces of data being sent than a few large chunks of data
	* provides **host-to-host** communication
* **Layer 3 - Network**
	* another header is added on at this layer
		* **the combination of original data + L4 header + L3 header is called a** **packet**
	* provides connectivity between end hosts on different networks (outside the LAN)
	* provides logical addressing (**the IP address of the data**)
	* provides path selection between source and destination
	* **routers** act at level 3
* **Layer 2 - Data Link**
	* L2 adds a **L2 trailer** to the data
		* **the addition of the L2 trailer to the packet creates a** **frame**
	* provides node-to-node connectivity and data transfer (PC to switch, switch to router, router to router)
	*  defines  how data is formatted for transmission over a physical medium (for example, copper UTP cables)
	* detects and potentially corrects Physical Layer errors
	* Uses L2 addressing, separate from L3 addressing
	* switches operate at L2; switches look at the destination L2 address to know where to send the data
* **Layer 1 - Physical**
	* sends the above **frame** over an electrical signal
	* defines physical characteristics of the medium used to transfer data between devices
		* voltage levels, maximum transmission distances, physical connectors, cable  specifications, etc.
	* digital bits are converted into electrical (for wired connections) or radio signals (for wireless connections)
* **protocol data units (PDU)= everything from the original data to the frame**
	* ![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/unknown_filename.4.png]]
	* **the segment is a L4 PDU; packet is a L3 PDU**
	* **Layer 1 PDU = bit**

**TCP/IP Suite**

* ![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/image.png]]
	
* conceptual model and set of communication protocols used in the internet and other networks
* known as TCP/IP as these are the two foundational protocols in the suite
* developed by the DoD via DARPA (Defense Advanced Research Projects Agency)
* Similar structure to the OSI model, but with fewer layers
* TCP/IP is actually used in modern networks, but the OSI model still influences how network engineers think and talk about networks

* ![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/unknown_filename.1.png]]

**Certain organizations use different names and have different layers for both the OSI model**

* ![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/unknown_filename.3.png]]

**Network Topology and Data Flow**

![[./_resources/Day_3_-_OSI_Model_and_TCPIP_Suite.resources/unknown_filename.png]]

**QUIZ**

1.  HTTP data sent from a YouTube web server is displayed via a web browser.  what is this an example of?

            - **same-layer interaction**

2. **HTTP data** has been encapsulated with three different headers and one trailer; what is the appropriate name for this PDU
	* **Frame**

3. which layers of the OSI model are the most relevant to a network engineer?
	* **Transport -> Network -> Data Link -> Physical**

4. the Link layer of TCP/IP is equivalent to what layer/layers of the OSI model?
	* **Data Link + Physical layer of OSI**

5. which layer of the OSI model provides host-to-host communications
	* **Layer 4, Transport layer**
