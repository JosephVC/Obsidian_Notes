---
source: https://static-labs.tryhackme.cloud/sites/ssrf-examples/
---
**What is SSRF**

* stands for **Server Side Request Forgery** 
* allows a malicious user to make an additional or edited HTTP request to whatever resource the attacker wants
* there are two types of SSRF vulnerabilities 
	* regular
		* data is returned to the attacker's screen
	* blind SSRF
		* no info is returned

**Example**

1. **![[./_resources/SSRF.resources/unknown_filename.png]]**
2. **![[./_resources/SSRF.resources/unknown_filename.3.png]]**
3. **![[./_resources/SSRF.resources/unknown_filename.1.png]]**
4. **![[./_resources/SSRF.resources/unknown_filename.2.png]]**
5. **![[./_resources/SSRF.resources/unknown_filename.4.png]]**

* In the above example we needed to trick the website into requesting our attack server and loading the flag
* **look at the difference in what the server is requesting with the "&x=" above** 
* the "&x=" string tells a server to not look at anything beyond that string, so the request effectively stops looking for anything else after we ask for the flag id
	* **![[./_resources/SSRF.resources/unknown_filename.5.png]]**
	* without the "&x=" the server is trying to look for and id of "**9.website.thm/api/item?id=2"** rather than simply 9, because the request wants to look at the entire address rather than where we cut it off

**Finding an SSRF**

* ![[./_resources/SSRF.resources/unknown_filename.6.png]]
* when working with a blind SSRF - where no output is reflected back to you - requests need to be monitored by an external HTTP request logging tool such as [requestbin.com](http://requestbin.com/) or Burb Suite's Collaborator tool

**Defeating Common SSRF Defenses**

* **Deny List**
	* all resources are **accepted** except those specified in a list or matching a particular pattern
	* sensitive endpoints can be protected by using a deny list 
	* a specific endpoint to be protected is localhost
	* you can **bypass a deny list** using alternative localhost references such as 0, 0.0.0.0, 0000, 127.1, 127.\*.\*.\*, 2130706433, 017700000001 or subdomains that have a DNS record resolving to 127.0.0.1, such as 127.0.0.1.nip.io
	* in a **cloud environment** it would be good to block 169.254.169.254; this contains metadata for the deployed cloud server, which may include sensitive information
		* an attacker can register this domain as their own subdomain with a DNS record that points back to their own domain
* **Allows List**
	* all requests are **denied** unless they match a particular pattern, such as foo.com
	* an attacker can **bypass an allow list** by creating a subdomain on the attacker domain, such as [foo.com.attacker-domain.com;](http://foo.com.attacker-domain.com%3B) this takes advantage of application logic and lets an attacker control the HTTP request
* **Open Redirect**
	* an endpoint on the server where a visitor gets automatically redirected to **another** website
	* a site could have an endpoint which simply records the number of people who've clicked certain links - www.foo.com/link?url=https://counter.com
		* if there was some SSRF vuln. where only sites beginning with [foo.com](http://foo.com) were allowed, then an attacker could try redirecting the above url to their own site
