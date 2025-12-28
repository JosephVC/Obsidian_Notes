---
---
* The **OSI** stands for **Open Systems Interconnection**
* is functionally a compact version of the TCP/IP model
* There are **seven layers** to the OSI model
	* Layer 7 - Application
		* provides network options to other programs running on the computer
		* works almost exclusively with applications, to provide them with an interface to transmit data which is then passed to the presentation layer
	* Layer 6 - Presentation
		* receives data from the application layer
		* while in a format applications can understand, data may not be in a standardized format which could be understood by the application of the receiving computer
		* the presentation layer does the above standardization in addition to any encryption, compression, and other transformation
	* Layer 5 - Session
		* when (correctly formatted) data gets received the session layer sees if a connection can be set up with the other computer across the network; otherwise and error message gets sent back and the process goes no further 
		* when a connection can be established, the session layer maintains it
			* it will communicate with the session layer of the other computer to synchronize communication
			* the session established is unique
		* the session layer is what allows you to make multiple requests to different endpoints simultaneously without data getting mixed up
			* like multiple tabs in a browser being open
		* when a successful connection is made the data is passed to layer 4
	* Layer 4 - Transport
		* first purpose is to determine which protocol is to be used to send data, then splits the data into portions
			* TCP (Transmission Control Protocol)
				* data portions are called segments
				* **Connection based** protocol which allows a continuous transmission for the duration of a request
					* allows for a more reliable transmission which can prioritize making sure all packets get to their destination, with constant communication kept between computers to make sure acceptable speeds are kept and any lost data is re-sent
			* UDP (User Datagram Protocol)
				* data portions are called datagrams
				* packets get sent to a receiving computer as fast as possible, with accuracy not a priority
	* Layer 3 - Network
		* responsible for locating the destination of the request
		* takes the IP address of a page and figures out the best way to send the information
		* this layer deals with **logical addressing**, meaning the IP addresses - which are software controlled
			* logical addresses are used to provide order to a network through categorization and sorting
				* 127.0.0.1 is a form of logical addressing in the IPV4 format
	* Layer 2 -  Data Link
		* focuses on the physical addressing of transmission
		* checks to make sure data has not been corrupted and presents the data in a format suitable for transmission 
		* a packet is received by the network layer (including the IP address of the remote computer) and the data link layer adds the physical MAC address of the receiving endpoint. 
		* Every network-enabled computer has a NIC (Network Interface Card) that has one of these unique MAC addresses on it for the purposes of identification. 
	* Layer 1 - Physical Layer
		* the physical hardware layer of a computer which send and receive the pulses of data being sent over the network;
		* this layer converts the binary data of transmission into signals ready for transmission as well converts these signals back into binary data
