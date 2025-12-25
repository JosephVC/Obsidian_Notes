---
---
**Basic Terms**

**role-based access controlled** - software written for a specific role, such as altering or creating bank accounts, but where regular users only have access to a small subset of features

**web application mapping** - map representing the structure, organization, and functionality of a web app

**zone transfer attack -** a recon tactic against badly configured DNS servers; this involves a specifically formatted request designed to look like a valid DNS zone transfer from a valid DNS server, all the while really being made on behalf of an individual

* the DNS system is what translates the IP address of something like 127.0.0.1 to a human-readable name like 'localhost'
* the DNS servers also allow the IP address of a site to change without having to update the application users on those servers, meaning one can go to [apple.com](http://apple.com/) without worrying where that name might actually take you, even if the IP address changes
* DNS servers are reliant on the ability to synchronize DNS record updates with other DNS servers ; this is a standardized way DNS servers can share records, which are shared in a text file called a **zone file** 
* a properly configured DNS server will only accept requests from other specifically defined DNS servers; one can pretend to be a DNS server to take advantage of mis-configured actual DNS servers
* first, use the DNS lookup utility **host (host** [whatever-site.com](http://whatever-site.com/) **for example) :**
	* **![[./_resources/Untitled_Note.resources/unknown_filename.png]]** 
* your next step would be to use the host command again, with the **\-l** flag and the address [nwk-aaemail-lapp03.apple.com](http://nwk-aaemail-lapp03.apple.com/) like so: **host -l** [apple.com](http://apple.com/) [nwk-aaemail-lapp03.apple.com](http://nwk-aaemail-lapp03.apple.com/)
	* if this worked it means the DNS server is **not** configured correctly; if the latter was configured correctly you'd get a connection failure:
		* ![[./_resources/Untitled_Note.resources/unknown_filename.1.png]]
	* most servers of big-name companies will be properly configured, but given how easy this was it's always worth trying
* If the above does not work you can **brute force** subdomains;
	* **this is easily detected and can screw you in the long run by getting  your IP banned by the server you're trying to force**
	* thus, brute force should be a last resort
	* a library called **dnscan** ships with millions of popular subdomains
		*  this library can be plugged into code that performs a **dictionary attack** to find subdomains
		* dictionary attacks are more efficient than brute force attacks

**Stored Cross-Site Scripting - XSS**

* when an application does not properly validate data and an attack is stored in the database
* when the above data is recalled by a user action, the attack is launched against the user

**Public Key Pinning** 

* a system created to protect against fraudulent certificates
* the idea is that only one or two Certificate Authorities could be trusted for a particular URL
* a trusted certificate would be pinned to a website and to a specific cryptographic identity (keys)
* a substantial problem with this approach is that if one loses their crypto keys, their site becomes unusable for up to a year
	* the above is called **HPKP Suicide** 
* this sort of practice is considered **deprecated**

**Secret Stores**

* like password managers for computer systems rather than people
* the store encrypts various secrets, then allows applications access to them programmatically 

**Service Accounts**

* used by computers rather than people and is the identity of the computer on a network rather than a person
* service accounts should be created when an application needs access to a database, rather than have a person's account connecting to the database
