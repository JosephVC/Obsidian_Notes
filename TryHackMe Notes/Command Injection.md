---
---
**Introduction**

* **command injection** is the abuse of an app's behavior to execute commands on the operating system, using the same privileges that the application on a device is running
	* if a user "bob" suffers a command injection attack, the attacker will be able to run commands under this user and have all their privileges 
* also known as a **Remote Code Execution (RCE)** vulnerability, where the attacker can remotely trick an application into running a series of payloads the attacker provides, all via a shell (no direct access to the machine itself)

**Discovering Command Injection**

* the vulnerability occurs because scripting languages pass data and make calls on the machine's OS
* ![[./_resources/Command_Injection.resources/unknown_filename.png]]
* any application where commands are being executed and the OS processes it

**Exploiting Command Injection**

* **blind command injection**
	* no direct output when testing payloads; you need to check the behaviour of applications to see if something worked
* **verbose command injection**
	* there is some direct feedback as to whether your injection worked
* **useful payloads**
	* ![[./_resources/Command_Injection.resources/unknown_filename.1.png]]
