---
---
**Cyber Threat Intelligence: Understanding the Environment**

* Cybersecurity Intelligence: How secure are we?
* Cyber Threat Intelligence: How threatening is the world outside

**Intelligence Sources**

* **Narrative Sources**
	* Look at what attacks are out there and have been used in the past
	* useful for when you need to buy specific equipment or expand your network
	* requires a lot of manual effort
* **Threat Feeds**
	* online source of data
	* provides continuous flow of information regarding threats

**Historical Trend Analysis**

* look for patterns in past incidents

**Reconnaissance**

* what could a potential attacker find out about us
	* Where would they look?
		* OSINT
			* the web
			* dedicated tools
				* [us-cert.gov/](http://us-cert.gov/)ncas
				* [otx.alienvault.com](http://otx.alienvault.com/)
				* [misp-project.org/feeds](http://misp-project.org/feeds)
		* virus research
			* <https://www.virustotal.com/gui/home/upload>
		* blogs
			* digitalguardian.com/blog/top-50-infosec-blogs-you-should-be-reading
			* feeds
		* Closed-source
			* collected and organized by security vendors
			* often subscription based
			* may be better maintained than open source (unless it is repackaged open source)
			* [exchange.xforce.ibmcloud.com](http://exchange.xforce.ibmcloud.com/)
			* [fireeye.com/mandiant/threat-intelligence/threat-intelligence-subscriptions.html](http://fireeye.com/mandiant/threat-intelligence/threat-intelligence-subscriptions.html)
			* <https://www.fortiguard.com/>
			* [talosintelligence.com](http://talosintelligence.com/)

**Whois & DNS**

* whois is a free public database for who controls certain websites
* DNS can be searched if you want alternate domains or internal domains of certain orgs
* nslookup
* dig
* host
* zone transfers
	* can be attempted on badly configured DNS servers
	* normally used to replicate a DNS database between multiple servers
	* sometimes this functionality is exposed, so you can request your own copy of a DNS server

![[./_resources/Part_05_Intelligence_Sources.resources/image.png]]

* <https://github.com/ElevenPaths/FOCA>
* <https://www.kali.org/tools/theharvester/>
* [shodan.io](http://shodan.io/)
* [maltego.com](http://maltego.com/)
* <https://www.kali.org/tools/recon-ng/>

**Website Rippers**

* clones a website's files to your machine
* may not copy database or backend files

**Google advanced search**

* Google Hacking Database

**Confidence Levels**

* is a source trustworthy?
* timeliness
	* info should not be old
* relevance
* accuracy
	* is a threat generic or specific
* fake news
	* is a source clickbait or real
* Admiralty system
	* ranks credibility and reliability of a source
	* <https://www.srmam.com/post/what-is-the-admiralty-scale>
	* https://irp.fas.org/doddir/army/fm2-22-3.pdf
