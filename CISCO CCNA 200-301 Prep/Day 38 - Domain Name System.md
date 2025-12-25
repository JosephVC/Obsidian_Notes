---
---
**The Purpose of DNS**

* used to resolve human-readable domain names (www.google.com) to IP addresses
* machines don't use names, but rather numbers like IP addresses; names are easier for people to remember
* when you type a URL name into a browser, your device will ask a DNS server for the IP address of the given website
* you can manually configure which DNS server your device uses, or it can be learned via **DHCP (Dynamic Host Configuration Protocol)**

**ipconfig/all**

* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.png]]

**nslookup**

* stands for 'name server lookup'
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.1.png]]

* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.2.png]]

![[./_resources/Day_38_-_Domain_Name_System.resources/image.3.png]]

* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.4.png]]

**DNS Cache**

* devices will save  a DNS server's responses to a local DNS cache; this  means they wont' have to query the server every single time they want to access a particular destination
* **canonical name -** another kind of DNS record that **maps a name to another name**
	* the canonical name may resolve to the same domain name
* you can flush the DNS cache with the command `ipconfig / flushdns`
	* your device will have to send a brand new query to the DNS server  if it wants a particular website
	* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.5.png]]

**Host File**

* most devices have a **hosts** file, which is a list of hosts and IP addresses
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.6.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.7.png]]

**DNS In Cisco**

* for hosts in a network to use DNS, you don't need to configure DNS on the routers; they will simply forward the DNS messages like any other packets
* However, a Cisco router can be configured as a DNS server (rare, though); If an internal DNS is used, usually its a Windows or Linux server
* a Cisco router can also be configured as a DNS client
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.8.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.9.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.10.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.11.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.12.png]]
* to see both configured and cached hosts, use the `show hosts` command
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.13.png]]
* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.14.png]]

QUIZ

* which Windows commands display a PCs DNS server?
	* `ipconfig /all`
	* `nslookup`

* which following statements about DNS are true
	* 'A' records map hostnames to IPv4 addresses
	* A cisco router can be configured as a DNS server and a DNS client at the same time

* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.15.png]]
	* to forward DNS queries and replies between servers, a router does not need any need any configuration; it will forward the packets as normal

* which of the following Cisco IOS commands shows the cached name/IP address mappings learned via DNS?
	*   `show hosts`

* Which following protocol can hosts use to automatically learn the address of their DNS server?
	* DHCP

* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.16.png]]
	* D) just the WWW server
		* normal DNS requests and responses are sent by using User Datagram Protocol (UDP) and do not result in TCP connections with the DNS server.
		* ![[./_resources/Day_38_-_Domain_Name_System.resources/image.17.png]]
