---
---
A web shell is a malicious script that allows an attacker to escalate an maintain persistent access on a web application which was already compromised.  it is considered part of the second stage of an attack as the web shell itself can't attack or exploit a remote vulnerability.  

The attacker initially takes advantage of a web page vulnerability - SQL injection, remote file inclusion (RFI) or cross-site scripting (XSS) in order to attain file upload capabilities and transfer malicious files.  the functionalities of the attack include shell command execution, code execution, database enumeration, and file management

Web shells can be written in any web language, such as PHP or Python.  Popular web-based apps are vulnerable, as are custom web apps.  Antivirus or anti-malware software may not detect a web shell as the latter do not always use executable file types.  Web shells are also available to the public, such as via github.

**Attacking a server**
A web shell can contain a backdoor allowing an attacker to remotely access an potentially control a web-facing server.  Each time access to the server is required, there is **no need to exploit a new vulnerability** on that server.  An attacker might actually fix vulnerabilities so no one else exploits them and the attacker can keep a lower profile.  

The shell itself may require authentication and other methods to ensure only the attacker has access to it.  The shell may have the capability to block search engines from listing the shell, thus obfuscating the shell.

**Privilege Escalation**
If a server is configured properly, the web shell will run with user-level permissions, thus prompting the need to escalate privileges via local vulnerabilities on the system. 

**Pivoting and Launching Attacks**
A web shell can be pivoted both inward and outside of a network.  Traffic can be sniffed and firewalls set up (over time, as the attacker wants to keep a low profile).  Scans and attacks can be sent outside the network as well, effectively giving the attacker a 3rd party to launch attacks from.  A skilled enough attacker would be able to hide behind multiple layers of exploited networks to hide their true location.  Servers can be made into a botnet of zombies, and the web shell used to control the botnet through a separate command-and-control server.  These sorts of networks can then be used to launch DDOS attacks.
