---
---
From **Alice and Bob Learn Web Application Security**

**Chapter 1**

* **![[./_resources/security_exercises.resources/unknown_filename.1.png]]**

* **assume breach:** prepare for a breach and design your system such that if someone gained unapproved access any action would be difficult and time-consuming, plus you would be able to log and monitor their actions
	* this can often be time consuming and not feasible for individuals
* **coordinated disclosure:** vulnerabilities are disclosed only after the vulnerability has been patched
* **defense in depth:** have multiple layers of security in case one or more fail
* **least privilege:** provide the absolute necessary amount of information and nothing more; if that information is obtained via unauthorized means, the attacker will get the bare minimum access
* **supply chain:** what actually goes into making something, such as an application; the majority of modern applications are made up of a variety of pre-written libraries and a small amt. of original code 
* **security by obscurity:** if something is hidden it will become more secure as it is less noticeable 
	* **obfuscation** is part of this tactic, making something harder to discern or read
* **attack surface reduction:** every part of an application exposed to potential attack is an attack surface, thus try to remove things from your application that are unrequired
* **hard coding:** values and credentials are put directly into source code
	* this can make the program's output unreliable and expose credentials in case someone gets access to the source code
* **never trust, always verify:** verify you have taken data from the correct source but never trust that data - always verify the data is appropriate for what the application ought to accept
	* ![[./_resources/security_exercises.resources/unknown_filename.png]]
* **usable security:**  people will find ways around security features too difficult to use
* **factors of authentication:** something you **know**, something you **are**, and something you **have** 

1\. Bob sets the Wi‑Fi setting on his pacemaker to not broadcast the name of
his Wi‑Fi. What is this defensive strategy called?

* obscurity

2\. Name an example of a value that could be hard coded and why. (What
would be the motivation for the programmer to do that?)

* API key; the programmer doesn't know how to create and draw variables from a separate (more secure) file 

3\. Is a captcha usable security? Why or why not?

* no, as it can be difficult for people with weak vision to discern the captcha

4\. Give one example of a good implementation of usable security.

* two-factor authentication, where in addition to a username/password the user's phone receives a separate code  
* a password manager, with one master password for the user to remember but which stores everything else for automatic retrieval 

5\. When using information from the URL parameters do you need to validate that data? Why or why not?

* yes, as the URL could be crafted maliciously to give an attacker unauthorized access

6\. If an employee learns a trade secret at work and then sells it to a competitor, this breaks which part(s) of CIA?

* confidentiality

7\. If you buy a “smart” refrigerator and connect it to your home network, then have a malicious actor connect to it and change the settings so that it’s slightly warmer and your milk goes bad, which part(s) of CIA did they break?

* integrity

8\. If someone hacks your smart thermostat and turns off your heat, which part(s) of CIA did they break?

* availability

9\. If a programmer adds an Easter egg (extra code that does undocumented functionality, as a “surprise” for users, which is unknown to management and the security team), does this qualify as an insider threat? If so, why?  If not, why not?

* yes, as the Easter egg itself could contain vulnerabilities an attacker could take advantage of

10\. When connecting to a public Wi‑Fi, what are some of the precautions that you could take to ensure you are doing “defense in depth”?

* do not go to any sites that request sensitive information - no banking, etc. - and ensure your browser has an extension to connect via HTTPS
* use a VPN
* if you are in an area where wifi can't be trusted - like a hacker con - you can use cellular data 

11\. If you live in an apartment with several roommates and you all have a key to the door, is one of the keys considered to be a “factor of authentication”?

* no, these are all the same type of authentication factor
* as all the keys are the same, one key won't identify anyone in particular; **identification needs to identify an individual not just some member of a group**

**Chapter 2**

List two more potential security requirements for a web application (which
are not already listed).
2\. List two more potential security requirements for an operating system in
a car.
3\. List two more potential security requirements for a “smart toaster.”
4\. List two more potential security requirements for an application that
handles credit cards.
5\. Which security requirement is the most valuable? Why is it the most valu‑
able one to you and/or your organization?
6\. If you had to remove one of the requirements from this chapter from a
web app project, which one would it be? Why?
