---
---
**Console Port Security - login**

* be default, no password is needed to access the CLI of a Cisco IOS device via the console port
* you can configure a password on the **console line**
	* a user will have to enter a password to access the CLI via the console port
* to start a console line, use the `line console 0` command
	* the value of having a single console line is that you can only have a single console connection
* ![[./_resources/Day_42_-_Secure_Shell.resources/image.png]]

**Console Port Security - local login**

* alternatively, you can configure the console line to require users to login using one of the configured usernames on the device
	* `username --some username-- secret --your password--`
	* ![[./_resources/Day_42_-_Secure_Shell.resources/image.1.png]]
		* note that the above set password of **ccna** does not apply **but the login local password does apply**
		* the `exec-timeout` command will log the user out after - per the above - 3 minutes and 30 seconds of inactivity

**Layer 2 switch - Management IP**

* L2 switches don't perform packet routing and don't build a routing table ; they aren't IP routing aware
* you can assign an IP address to a **Switch Virtual Interface (SVI)** to allow remote connections to the CLI of the switch (via Telnet or SSH)
* ![[./_resources/Day_42_-_Secure_Shell.resources/image.2.png]]

**Telnet (Teletype Network)**

* protocol used to remotely access the CLI of a remote host
* Telnet was developed in 1969
* due to security reasons, largely supplanted by SSH
* **Telent sends data in plaintext with no encryption**
	* ![[./_resources/Day_42_-_Secure_Shell.resources/image.3.png]]
* the Telnet server listens for Telnet traffic on **TCP port 23**

**Telnet Configuration**

![[./_resources/Day_42_-_Secure_Shell.resources/image.4.png]]

* verifying configuration
	* ![[./_resources/Day_42_-_Secure_Shell.resources/image.5.png]]

**SSH (Secure Shell)**

* SSH was developed in 1995 to replace less secure protocols like Telnet
* SSHv2, a major revision, was launched in 2006
* if a device supports both v1 and v2, it is said to run 'version 1.99'
* Provides security features such as data encryption and authentication
* **SSH servers (the device being connected to) uses TCP port 22**

**SSH Configuration: Check SSH Support**

* ![[./_resources/Day_42_-_Secure_Shell.resources/image.6.png]]
* IOS images that support SSH will have **K9** in their name
* the `show ip ssh` will show you the **version** of SSH
* **you need a key length of at least 768 bits**
* Cisco exports NPE (No Payload Encryption) IOS images to countries that have restrictions on encryption technologies
* NPE IOS images do not support cryptographic features such as SSH
* the RSA keys highlighted above are cryptographic keys essential for the security features of SSH

**SSH Configuration: RSA Keys**

* to enable the use of SSH, you must generate an RSA public and private key pair
* the keys are used for data encryption/decryption, authentication, etc.
* ![[./_resources/Day_42_-_Secure_Shell.resources/image.7.png]]
	

**SSH Configuration: VTY Lines**
![[./_resources/Day_42_-_Secure_Shell.resources/image.8.png]]

**SSH Configuration Hostname Overview**

1. configure host name-

* a device needs a valid hostname - not just the default hostname - to generate its own RSA keys
* ![[./_resources/Day_42_-_Secure_Shell.resources/image.9.png]]
	

1. configure DNS domain name
2. Generate RSA key pair
3. Configure  and enable username and password
4. Enable SSHv2 (only)

* using v2 is considered best practice

    5.  Configure VTY lines

* ensure `transport input ssh` is enabled before anything else, and then configure other

    6.  **connect via SSH using** `ssh -l --username-- --ip address--` **OR**  `ssh --username@ip-address` 

**It is essential for the exam to know how to configure SSH**

**Command Summary**
![[./_resources/Day_42_-_Secure_Shell.resources/image.10.png]]

QUIZ

![[./_resources/Day_42_-_Secure_Shell.resources/image.11.png]]

* a,e
	* you need a hostname and a DNS domain name configured before generating an RSA key

![[./_resources/Day_42_-_Secure_Shell.resources/image.12.png]]

* C), D)

![[./_resources/Day_42_-_Secure_Shell.resources/image.13.png]]

* b
	* ssh uses TCP port 22, and the other answers either did not use tcp or did not use port 22
	* you must use the `access-class` command to apply the ACL

![[./_resources/Day_42_-_Secure_Shell.resources/image.14.png]]

* b, F

![[./_resources/Day_42_-_Secure_Shell.resources/image.15.png]]

* b
	* the server is the device **being connected to**

![[./_resources/Day_42_-_Secure_Shell.resources/image.16.png]]

* B
	* even after you define a host name, you still need to define a domain-name
	* ![[./_resources/Day_42_-_Secure_Shell.resources/image.17.png]]
	* ![[./_resources/Day_42_-_Secure_Shell.resources/image.18.png]]
