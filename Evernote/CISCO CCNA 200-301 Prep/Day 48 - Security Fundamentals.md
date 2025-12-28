---
---
**Why security**

* the principles of CIA Triad form the foundation of security
	* **Confidentiality**
		* only authorized users should be able to access data
		* some information is public and can be accessed by anyone, some is secret and should only be accessed by specific people
	* **Integrity**
		* Data should not be tampered with (modified) by unauthorized users
		* data should be correct and authentic
	* **Availability**
		* the network/systems should be operational and accessible to authorized users
* attackers threaten all the above

**vulnerability, exploit, threat, mitigation**

* a vulnerability is any potential weakness that can compromise the CIA of a system
	* a potential weakness isn't a problem on its own
* an exploit is something that can potentially be used to exploit a vuln.
	* a potential exploit isn't a problem on its own
* a threat is the potential of a vulnerability to be exploited
	* an attacker exploiting a vulnerability in your system is a **threat**
* a mitigation technique is something that can protect against threats
	* anywhere a vulnerability can be exploited should have a mitigation technique

**Common Attacks**

* **DOS**
	* threaten availability
	* the **TCP SYN flood** is a common technique
		* TCP three-way handshake: SYN  SYN-ACK  ACK
		* the attacker sends countless TCP SYN messages to a target
		* the target sends a SYN-ACK message in response to each SYN it receives
		* the attacker never replies with the final ACK, so the target keeps waiting
		* the target's TCP connection table thus fills up and the target is no longer able to make legitimate TCP connections
		* the attacker is likely to spoof their IP address so that no SYN-ACK messages reach them
			* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.png]]

* in a **DDOS**, an attacker infects many target computers with malware and uses them all to initiate a DOS attack
	* the computers infected by malware used for this purpose are called a **botnet**

* **Spoofing Attack**
	* using a fake address (IP, or MAC address)
	* many attacks will use spoofing
	* an example  is a **DHCP exhaustion** attack
		* the attacker uses spoofed MAC addresses to flood DHCP Discover messages
		* the target server's DHCP pool becomes full, resulting in a denial of service attack
		* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.2.png]]
* **Reflection/Amplification**
	* in a **reflection** attack, the attacker sends traffic to a **reflector**, and spoofs the source address of its packets using the target's IP address
	* the **reflector** (such as a DNS server) sends the reply to the target's IP address
	* if the amount of traffic sent to the target is large enough, this can result in a denial-of-service
	* a reflection attack becomes an **amplification** attack when the amount of traffic sent by the attacker is small, but triggers a large amount of traffic to be sent form the reflector to the target
	* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.1.png]]
* **Man in the middle**
	* an attacker places themselves in the middle of a communication, or to modify traffic before it reaches its destination
	* a common example if **ARP spoofing/ARP poisoning**
		* the host sends an ARP request, asking for the MAC address of another device
		* the target sends an ARP reply, informing the request of the MAC address
		* the attacker waits and then sends another ARP reply after the legitimate replier
		* if the attacker's ARP reply arrives last, it overwrites the legitimate ARP entry in PC1's ARP table
		* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.3.png]]
		* now, PC1's ARP table, the entry for 10.0.0.1 will have the attacker's MAC address
		* when PC1 tries to send traffic to SVR1 it will be forwarded to the attacker instead, so the attacker now has access to PC1's messages
		* the attacker can also modify messages before forwarding them
		* this attack compromises both **confidentiality** and **integrity**
		* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.4.png]]
* **reconnaissance attack**
	* used to gather information about a target for a future attack
	* figuring out IP address, email addresses, etc.
* **malware**
	* refers to a variety of harmful programs that can infect a computer
	* **viruses** require a host program
	* **worms** don't require a host program and can spread on their own
	* **trojan horse** disguised as legit software
* **social engineering attacks**
	* target people
	* psychological manipulation
		* **phishing**
			* **spear fishing** more targeted form of phishing
			* **whaling** targets VIPs
		* **vishing -** phishing via voice
		* **smishing**  is phising via SMS text
	* **watering hole** - sites commonly visited by the target are compromised
* **password-related attacks**
* ![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.5.png]]

**Multi-factor authentication**

* requires more than just a username/password for validation

**Digital certificates**

*  certificates are used to authenticate and prove the identity of the holder of the cert.
* they are to verify that a website is being accessed is legitimate
* entities that want a certificate to prove their identity send a **CSR (Certificate Signing Request)** to a **CA (Certificate Authority)**, which will verify and sign the certificate

**Controlling and Monitoring Users with AAA**

* **AAA** stands for Authentication, Authorization, Accounting
* a framework for controlling and monitor users of a computer system
* **authentication**  is the process of verifying a user's identity 
* **authorization** is the process of granting the user the appropriate access and permissions
* **accounting** is the process of recording the user's activities on the system
	* **logging** is a good example of this
* enterprises typically user AAA server to provide AAA services
	* ISE (Identity Services Engine) is Cisco's AAA server
* AAA servers usually support the following two AAA protocols
	* RADIUS - an open standards protocol using UDP ports 1812 and 1813
	* TACACS+ - a cisco proprietary protocol using TCP port 49

**Security Program Element**

* **user awareness** programs are designed to make employees aware of potential security threats and risks
	* a company might send out false phishing emails to test employee's awareness of security
* **user training** programs are more formal than user awareness programs
	* dedicated training sessions
* **physical access control** protects equipment and data from potential attackers by only allowing authorized users into protected areas such as network closets or data center floors
	* multifactor locks (badge + fingerprint)

**QUIZ**

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.6.png]]

* **D**

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.7.png]]

* A

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.8.png]]

*     d, c

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.9.png]]

* c

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.10.png]]

* d

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.11.png]]

* C, E

![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.13.png]]![[./_resources/Day_48_-_Security_Fundamentals.resources/unknown_filename.12.png]]
