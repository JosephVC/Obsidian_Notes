---
---
**What is a CLI?**

* Command Line Interface
* the interface needed to configure CISCO devices
* contrasted with a GUI (Graphical User Interface)

**How to Connect to a CISCO device**

* You will often need to physically connect to the the console port of a CISCO device
* there may be ways to wirelessly connect to the device as well
	* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.2.png]]
		* Assuming you'll want to connect to the RJ45 port, you'll need a special cable with an RJ45 on one end and a **DB9 connector** on the other; most laptops don't have serial ports so you'll need an adapter
		* this type of cable is called a **rollover cable**
			* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.6.png]]
			* the rollover cable pins connect like  in reverse
				* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.1.png]]
	* You need a **terminal emulator** such as **PuTTY** to access the CLI
		* just make sure you have the correct connection type figured

**User EXEC Mode**

* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.3.png]]

**Privileged EXEC Mode**

* enter the **"enable"** command in the User EXEC Mode to enter the privileged mode
* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.4.png]]

**comparisons between user and privileged modes**

* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.7.png]]

**the CLI can auto-complete certain commands; you can also hit the Tab key to auto-complete**

* if multiple commands begin with a certain letter or combination of letters, you may get the **"% Ambiguous Command"** error

**Global Configuration Mode**

* need to make changes to a router's configuration
* command needed is **configure terminal** or **conf t**
* you can control access to global configuration mode with a password (case sensitive) with the command **enable password**
	* note the difference between having a **"?"** after **password** with and without a space
	* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.png]]
	* the password will not be displayed as you type it
	* if you enter the wrong password 3 times, you'll see the output **Bad secrets**

**running-config/startup-config**

* there are two separate configuration files kept on the device at once
	* **running-config:** the current, active configuration file running on the device; as you enter commands in the CLI, you edit the active configuration
		* **startup-config:** the configuration file that will be loaded upon restart of the device
		* use the command **show running-config** or **show startup-config**

**service password-encryption**

* this command is used to hide your password
* rather than display the password in plain text, the password is encrypted so that when it does show with the **"7"** flag set after **enable password**, all you see are the encrypted characters; the 7 refers to CISCO's proprietary encryption algo
* ![[./_resources/Day_4_-_Intro_to_CISCO_IOS_CLI.resources/unknown_filename.5.png]]
* the CISCO encryption established by the 7 command can be easily cracked, **so it's better to use the "5" flag instead**
	* 5 refers to MD5 encryption

**Cancelling Commands**

**QUIZ**

1. What kind of cable is used to connect to a CISCO device via the RJ45 console port?

* rollover cable

2. you type **enable** to enter privileged exec mode on your CISCO router, however the password entered is not accepted.  what could be the problem

* **you likely have your caps lock on**
* the option of **service password encryption** simply encrypts the password and changes how it is displayed but would not change it, so the issue comes down to what the user is entering

3. what is the most secure method to protect access to privileged EXEC mode?

* use the **enable secret** command
	* simply **enable password** configures a plain-text password which is visible and not secure
	* the **service password-encryption**  sets weak encryption

4. if both **enable password** and **enable secret** command are configured, what will happen when **enable** is used to enter privileged EXEC mode

* you must enter the **enable secret** only
	* the **enable secret** always takes precedence over the **enable password**

5. you enter **conf t** to enter global configuration mode; what is the full name of this command? - **configure terminal**
