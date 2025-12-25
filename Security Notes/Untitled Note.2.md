---
---
**OWASP**

**OWASP** stands for Open Web Application Security Project and is a nonprofit foundation

OWASP Top 10

* a report released every 3-4 years drawn from security firms
* represents vulnerabilities drawn from hundreds to thousands of organizations encompassing thousands of applications
*  selected by:
	* prevalence of data
	* exploitablility
	* detectability
	* impact to organizations
* review of the top 10 vulnerabilities re: the above based on prevalence and detectibility
* how to prevent these attacks

**OWASP 2017**

1. Injection
	*  when a user access a web application, typing their username/password, these credentials are passed to a database to verify the creds
	* the language to query the database tends to be SQL, and it's possible to inject SQL into the credentials fields to gain improper access to the system
	* always assume user-input is untrusted
	* **to protect against this**
	* you can use query parameterization - there are parameters to the commands sent from the front end to the database; separate the SQL statements from the parameters to any callbacks from the database
	* validate user input to ensure the user is entering nothing dangerous
	* LIMIT - have limiting commands in the database to ensure that, if there is exposure, the data being exposed is limited 
2. Broken Authentication

* so a user inputs credentials to log in, and these creds are stored in a database
* if this authentication is successful, a session ID is provided for the session the  user signed in to use the web app
* if the web app is not built properly, an attacker could use various tactics to gain access
	* credential stuffing: stolen creds are used to access the web application
	* automated attacks: random usernames and passwords are thrown at the web app to gain access
	* default passwords: there may be default passwords set which could be guessed or found out
* **to protect against this** 
	* multi-factor authentication: there is another form of authentication beyond username/password, such as a key sent to a user, biometric scan, etc.
	* password checking: check username/passwords against a list of common creds, and alert a user their creds may be too common
	* password complexity: force the password to be of a certain length and complexity
	* limit failed login: if there are too many failed login attempts, the account is locked out
	* server side session management:  on the back end of the web app; a session ID manager is set up which creates a second random session ID rather than the initial (single) session ID; this prevents an attacker from using that initial session ID to gain control 

1. Sensitive Data Exposure

* one way or another, someone allows sensitive data to be exposed
* attackers will want to expose this sensitive information 
* an attacker could force HTTPS to HTTP
* attacker could use a rainbow table - table of known list of cracked passwords 
* **to protect against this**
	* classify data
		* not all data is sensitive, so classify it as such
		* apply controls to the data that is actually sensitive
	* encrypt data at rest (data that is sitting in the database)
	* use strong cyphers
	* PFS (Perfect Forward Security)
		* deals with the TLS connection
		* stronger form of communication using the TLS protocol between the user and the web server
	* HSTS (HTTP Strict Transport Security)
		* says that if someone wants to communicate with my web app, it must be done via HTTPS
	* web application firewall

1. XXE

* XML External Entities
* takes advantages of XML parsers in the web application to parse bad data
* say a web app uses an XML parser that accepts XML directly
	* these XML documents can contain references to external entities; an attacker can put malicious code in the external reference which could get run by the web app
* Billion Laughs attack
	* an attacker creates an XML file that forces the host machine to burn through a large amt. of memory
* **to protect against this**
	* disable XXE on the web app
	* disable DTD processing
	* implement server-side input validation
	* source code analysis 
	* dynamic application security testing - DAST -  to be run against your web app
	* implement a web application firewall if the web app itself can't have its issues corrected

* Broken Access Control
	* controlling the resources a user does need or should not have access to
	* there are different types of users who can access only certain parts of the web app
	* **to protect against this**
		* manual testing
		* have trusted server-side code that checks access
		* deny by default; only allow the basics of the app to be seen and deny the rest without special access
		* re-use access controls - that work - across the web application
		* log failures to access parts of the web app
		* rate limit access to sensitive areas
		* least privilege - give people the least amt. of access for the least amt. of time to do a job 
* Security Misconfiguration
	* don't use what you don't need
	* keeping default passwords/settings which are already widely known
	* there may be an absence of security headers used when communicating to the client
	* error pages that send specific configuration information to the public
	* **to protect against this**
		* automated scanning tool
			* django has this
		* repeatable hardening processes - harden the web application against the above, repeatedly 
		* all servers need the same configuration; don't have one hanging out with different features that may be vulnerable
		* minimal platform
			* turn off the features you don't need
		* Security directives
			* HSTS, HPKP, X-Frame options

* XSS (Cross Site Scripting)
	* client side code injection
	* an attacker sends code they want your browser to execute in order to provide the attacker with data
	* three requirements for an XSS attack
		* Attacker
			* wants to find a web app vulnerable to XSS
			* will POST a script to demand a cookie from the victim
				* posts the script to the database via the website 
		* Web app
			* has HTML code + a database
				* suppose that HTML allows scripts to be run
		* victim 
	* to protect against this
		* use a modern browser
		* separate untrusted data from active browser content when building the web app
		* web app firewall in front of web app
*  Insecure Deserialization
	* start with serialization; take an object and transfer it into a byte stream so that object can be in the proper format in order to traverse an HTTP network OR stored in a database
		* you can persist the state of an object when sending it over HTTP
		* deserialization is when you take the byte stream and turn it back into an object
	* if you take untrusted user input, don't bother validating it, and then allow it to be deserialized, an attacker can insert malicious code/object into the web app 
	* potentially, remote code could be run this way, or a DDOS
	* this is hard to find out, and will involve a variety of scanning and human interaction
	* **to protect against this**
		* do not accept untrusted user input
		* web app firewall
* Using Components with Known Vulns
	* it's not always easy to pick a component that has no known vulnerabilities 
	* theoretical web app components
		* Apache web server
			* struts vuln
		* Oracle DB server
			* Java VM vulnerability
		* TLS/SSL/HTTPS
			* Heartbleed vuln
				* still 120,000 web apps vulnerable to this
	* **to protect against this**
		* continuous inventory of clients and servers
		* download components front trusted/official sources
		* plan for regular monitoring, patching, configuration
		* Keep in mind the CVE - Common Vulnerabilities and Exploits - and NVD - National Vulnerabilities Database
*  Insufficient Logging & Monitoring 
	* so you have your web app, and if there is a failed login it **creates an event**, which in turn creates a **log entry**
	* OWASP has a cheat cheat of log entries one should look out for
	* make sure an attacker can't get access to the logs
	* you don't want any serious lag time between an attack appearing in the logs and someone actually seeing those entries
	* **to protect against this**
		* regularly check your logs
		* have sufficient content
			* any login failure or server-side failure needs to be logged
			* make sure the logs are in a good format that is easily read by a person or automated service
			* balance between having too much/too little information
			* ensure you have integrity controls
				* make sure there is a way to track changes to the log file in case it is compromised 
			* have a response plan 
				* constantly monitor the logs in case there is a breach
