---
---
**Wireless Network Security**

* security is more essential to wireless networking
	* because wireless signals are not contained within a wire, any device within range of the signal can receive traffic
	* in wired networks, traffic is often only encrypted when sent over an untrusted network such as the internet
	* in wireless networks it is crucial to encrypt traffic sent between the wireless clients and the AP

**Authentication**

* all clients must be authenticated before they can associate with an AP
* in a corporate setting, only trusted users/devices should be given access to the network
	* in corporate settings, a separate SSID which does not have access to the corporate network can be provided for guest users
* ideally, clients should also authenticate the AP to avoid associating with a malicious AP
* there are multiple ways to authenticate
	* password
	* username + password
	* certificates
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.png]]

**Encryption**

* traffic sent between clients and APs should be encrypted so that it can't be read  by anyone except the AP and the client
* there are many possible protocols that can be used to encrypt traffic
* all devices on the WLAN will use the same protocol, but each client will use a unique encryption key so that other devices can't read its traffic
* a 'group key' is used by the AP to encrypt traffic that it wants to send to all clients .
	* all the clients associated with the AP keep that key so they can decrypt the traffic

**Integrity**

* Integrity ensures that a message is not modified by a third-party.  the message that is sent by the source host should be the same as they message that is received by the destination host
* a **MIC (Message Integrity Check)** is added to messages to help protect their integrity
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.1.png]]

**Authentication Methods**

* **Open Authentication**
	* one of the original 802.11 authentication standards
	* the client sends an authentication request, and the AP accepts it with no questions
	* **very insecure**
	* after the client is authenticated and associated with the AP, it's possible to require the user to authenticate via other methods before access to the network is granted (i.e starbucks wifi)
* **WEP (Wired Equivalent Privacy)**
	* the second 802.11 standard
	* used to provide both authentication and encryption of wireless traffic
	* for encryption, WEP uses the RC4 algorithm
	* WEP is a **shared-key protocol** requiring the sender
	* WEP keys can be a 40 bits or 104 bits in length
		* the above keys are combined with a 24-bit **IV (Initialization Vector)** to bring the total length to 64 bits or 128 bits
	* **WEP is not secure and can be easily cracked**
	* WEP can be used for **authentication**
		* ![[./_resources/Day_57_-_Wireless_Security.resources/image.2.png]]
		
* **EAP (Extensible Authentication Protocol)**
	* not an authentication method by itself but a **framework** which other **EAP methods** are based on
	* defines an authentication functions that are used by the various EAP methods
	* EAP is integrated with 802.11X, which provides **port-based network access control**
		* 802.11X:  used to limit network access for clients connected to a LAN or WLAN until they authenticate
		* **three main entities in 802.11X**
			* **Supplicant:**  the device that wants to connect to the network (the client)
			* **Authenticator:**  the device that provides access to the network
			* **Authentication Server:**  the device that receives client credentials and permits/denies access
			* ![[./_resources/Day_57_-_Wireless_Security.resources/image.3.png]]
				
* **LEAP (Lightweight EAP)**
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.4.png]]
		
	* developed by CISCO as an improvement over WEP
	* clients must provide a username+password to authenticate
	* also, **mutual authentication** is provided by both the client and server sending a challenge phrase to each other
	* **dynamic WEP** keys are used, meaning that the WEP keys are changed frequently
	* **like WEP, LEAP is considered vulnerable and should no longer be used**
* **EAP-FAST (EAP Flexible Authentication via Secure Tunneling)**
	* developed by CISCO
	* consists of 3 phases
		1. a **PAC (Protected Access Credential)** is generated and passed from the server to the client
		2. a secure **TLS tunnel** is established between the client and authentication server
		3. inside the secure, encrypted, tunnel, the client and server communicate further to authenticate/authorize the client
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.5.png]]
		
* **PEAP (Protected EAP)**
	* like EAP-FAST, PEAP involves establishing a secure TLS tunnel between the client and server
	* instead of a PAC, the server has a digital certificate
	* the client uses this digital certificate to authenticate the server
	* the certificate is also used to establish a TLS tunnel
	* because only the server provides a certificate for authentication, the client must still be authenticated within the secure tunnel, for example using **MS-CHAP (Microsoft Challenge-Handshake Authentication Protocol)**
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.6.png]]
		
* **EAP-TLS (EAP Transport Layer Security)**
	* where PEAP only requires the AS to have a certificate, EAP-TLS requires a certificate on the AS and on every single client (supplicant)
	* EAP-TL is the **most secure** wireless authentication method, but it is **more difficult to implement than PEAP** because every client device needs a certificate
	* because the client and server authenticate each other with digital certificates, there is no need to authenticate the client within the TLS tunnel
	* the TLS tunnel is still used to exchange encryption key information
	* ![[./_resources/Day_57_-_Wireless_Security.resources/image.7.png]]
		

**Encryption and Integrity Methods**

* **TKIP (Temporal Key Integrity Protocol)**
	* WEP was found to be vulnerable but wireless hardware at the time was built to use WEP
		* a temporary solution was needed until a new standard was created and new hardware was built
	* TKIP adds various security features
		* a **MIC** is added to protect the integrity of messages
		* a **key mixing algorithm** is used to create a unique WEP key for every frame
		* the **initialization vector** is doubled in length from 24 bits to 48 bits, making brute-force attacks much more difficult
		* the MIC includes the **sender MAC address** to identify the frame's sender
		* a **timestamp** is added to the MIC to prevent replay attacks.  Replay attacks involve re-sending a frame that has already been transmitted
		* a **TKIP sequence number** is used to keep track of frames sent from each source MAC address.  this also protects against replay attacks
	* TKIP is used in WPA v.1
* **CCMP (Counter/CBC-MAC Protocol)**
	* CCMP was developed after TKIP and is more secure
	* is used in WPA2
	* to use CCMP, it must be supported by the device's hardware.  Old hardware built only to use WEP/TKIP cannot use CCMP
	* CCMP consists of two different algorithms to provide encryption and MIC
		* **AES (Advanced Encryption Standard) counter mode** encryption
			* AES is the most secure encryption protocol currently available.  It is widely used all over the world
			* there are multiple modes of operation for AES.  CCMP uses **counter mode**
		* **CBC-MAC (Cipher Block Chaining Message Authentication Code)** is used as a MIC to ensure the integrity of messages
* **GCMP (Galois/Counter Mode Protocol)**
	* more secure and efficient than CCMP
	* the increased efficiency allows higher data throughput than CCMP
	* used in WPA3
	* GCMP consists of two algorithms
		* **AES counter mode** encryption
		* **GMAC (Galois Message Authentication Code)** is used as a MIC to ensure the integrity of messages

![[./_resources/Day_57_-_Wireless_Security.resources/image.8.png]]

**Wifi Protected Access**

* the wifi alliance has developed three WPA certifications for wireless devices
	* WPA
	* WPA2
	* WPA3
* to be WPA certified, equipment must be tested in authorized testing labs
* all of the above support two authentication modes
	* **Personal mode:**  a pre-shared key (PSK) is used for authentication.  When  you connect to a home wifi network, enter the password and are authenticated, that is **personal** mode.  this is common in small networks
		* the PSK itself is not sent over the air.  a four-way handshake is used for authentication, and the PSK is used to generate encryption keys
	* **Enterprise mode:**  802.11X is used with an authentication server (RADIUS server)
		* no specific EAP method is specified, so all are supported (PEAP, EAP-TLS, etc.)
* the **WPA** certification was developed after WEP was proven to be vulnerable and includes the following protocols
	* TKIP (based on WEP) provides encryption/MIC
	* 802.1X authentication (Enterprise mode) or PSK (Personal mode)
* **WPA2** was released in 2004 and includes the following protocols
	* CCMP provides encryption/MIC
	* 802.1X authentication (Enterprise mode) or PSK (personal mode)
* **WPA3** was released in 2018 and includes the following protocols
	* GCMP provides encryption/MIC
	* 802.1X authentication (Enterprise mode) or PSK (personal mode)
	* WPA3 also provides several additional security features
		* **PMF (Protected Management Frames),** protecting 802.11 management frames from eavesdropping/forging
		* **SAE (Simultaneous Authentication of Equals)** protects the 4-way handshake when using personal mode authentication
		* **Forward secrecy:** prevents data from being decrypted after it has been transmitted over the air.  So, an attacker can't capture wireless frames and then try to decrypt them later

**QUIZ**

* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.png]]
	* b

* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.1.png]]
	* A, D, E

* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.2.png]]
	* C
* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.3.png]]
	*  D

* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.4.png]]
	* A

![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.5.png]]

* B
* ![[./_resources/Day_57_-_Wireless_Security.resources/unknown_filename.6.png]]
