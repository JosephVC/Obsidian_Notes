---
source: https://tryhackme.com/room/introtonetworking
---
Similar to the OSI model.  While older, still serves as the basis of real-world networking.  The layers of TCP/IP are **Application, Transport, Internet, Network Interface.**

Why use the OSI model if TCP/IP is the actual standard?  OSI can be easier to understand as it's more explicit in breaking down the layers.  Either way, the two models are very similar:

![[./_resources/TCPIP_Model.resources/unknown_filename.png]]   **Traceroute** runs on the **Internet** layer.

Encapsulation and de-encapsulation work the same way under TCP/IP, in that a header is added during encapsulation and removed during de-encapsulation.

The **TCP (**Transmission Control Protocol) controls the flow of data between two endpoints. The **IP** (Internet Protocol) controls how packets are addressed and sent.

**TCP**

* connection based protocol
* before you send any data via TCP you need to establish a stable connection between the given computers
	* the above is called a **three-way handshake**
		* to establish this handshake a computer must first send a  special request called a **SYN** ( _**synchronise**_ bit) (this is the British spelling) to make first contact with another computer
		* the other computer will respond with a packet containing the original SYN bit along with an ACK (acknowledgement bit) 
		* finally, the originating computer will send a packet containing the ACK bit itself, which confirms a successful connection and ability to reliably send data
			* any data that is lost or corrupted

![[./_resources/TCPIP_Model.resources/unknown_filename.1.png]]

The OSI and TCP/IP standards were implemented to correct for an lack of standards and manufacturers creating their own implementations, leading to incompatibilities between different hardware.  TCP/IP was introduced in 1982 to sort out these incompatibility problems.  OSI was introduced by the ISO standards body, but is considered an informal teaching guide, with TCP/IP being the official model actual in-use networks are based on.
