---
source: https://tryhackme.com/room/dnsindetail
---
**Domain Hierarchy**

![[./_resources/DNS.resources/unknown_filename.png]]
**TLD (Top Level Domain)**

* there are two types of TLD
	* **gTLD (Generic Top Level Domain)** : meant to tell a user a domain's purpose (.com for business, .org or an organization, .edu for education, etc.)
	* **ccTLD (Country Code Top Level Domain):** done for geographical purposes; currently there  is a large  number of ccTLDs (.biz, .online, etc.)

**Second-Level Domain**

* with [google.com](http://google.com) as the example, **.com** is the TLD and the **google** is the **Second-Level Domain**
* **length of 63 characters plus the TLD using a-z and 0-9, with hyphens**

**Subdomain**

* to the left-hand side of the second-level domain with a dot to separate them, such as maps.google.com, or [admin.tryhackme.com](http://admin.tryhackme.com)
* subject to the same length limits as second-level domains
	* while  you can chain multiple subdomains with periods, the total length must be 253 characters or less
	* there is no limit to the number of subdomains per se

**DNS Record Types**

* **A record:** resolve to IPv4 addresses
* **AAAA records:** resolve to IPv6 addresses
* **CNAME records :** resolve to another domain name
	* an online shop might have the address store[.address.com](http://foo.address.com) returns a CNAME record [shop.address.com](http://shop.address.com%3B)
	* another DNS record would then be made to [shop.address.com](http://shop.address.com) to figure out the IP address
* **MX records:** resolve to the IP address of the servers handling email for the domain being queried
	* the MX records for [foo.com](http://foo.com) would look like  [alt1.aspmx.l.google.com](http://alt1.aspmx.l.google.com)
	* these records have a priority flag, telling the client which server to try, such as when in case a main server goes down 
* **TXT records:** free text fields for recording text-based data
	* a common use is to list servers who can send email on behalf of a domain (useful for combating spam or spoofed emails)
	* can also help verify ownership of a domain name when signing up for third-party services

**What happens when you make a DNS request**

1. When you request a domain name, your computer first checks its local cache to see if you've previously looked up the address recently; if not, a request to your Recursive DNS Server will be made.
2. A Recursive DNS Server is usually provided by your ISP, but you can also choose your own. This server also has a local cache of recently looked up domain names. If a result is found locally, this is sent back to your computer, and your request ends here (this is common for popular and heavily requested services such as Google, Facebook, Twitter). If the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers.
3. The root servers act as the DNS backbone of the internet; their job is to redirect you to the correct Top Level Domain Server, depending on your request. If, for example, you request [www.tryhackme.com](http://www.tryhackme.com/), the root server will recognise the Top Level Domain of .com and refer you to the correct TLD server that deals with .com addresses.
4. The TLD server holds records for where to find the authoritative server to answer the DNS request. The authoritative server is often also known as the nameserver for the domain. For example, the name server for [tryhackme.com](http://tryhackme.com/) is [kip.ns.cloudflare.com](http://kip.ns.cloudflare.com/) and [uma.ns.cloudflare.com](http://uma.ns.cloudflare.com/). You'll often find multiple nameservers for a domain name to act as a backup in case one goes down.
5. An authoritative DNS server is the server that is responsible for storing the DNS records for a particular domain name and where any updates to your domain name DNS records would be made. Depending on the record type, the DNS record is then sent back to the Recursive DNS Server, where a local copy will be cached for future requests and then relayed back to the original client that made the request. DNS records all come with a TTL (Time To Live) value. This value is a number represented in seconds that the response should be saved for locally until you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.
