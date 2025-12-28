---
---
**nslookup and dig**

* nslookup stands for **Name Server lookup**
* below are the query types that can be used with **nslookup**
* **DNS record types**
	* ![[./_resources/Passive_Reconnaissance.resources/image.png]]
		* **TXT records:** these are a type of DNS record that contains text information for sources outside your domain; you can use these records to verify domain ownership
* dig stands for **Domain Information Groper**
	* dig can return more information than nslookup
	* normally just use "dig DOMAIN\_NAME" but you can also use "dig DOMAIN\_NAME TYPE"
		* you can also select the server to use with 'dig @SERVER DOMAIN\_NAME TYPE"
		* TYPE refers to the DNS record type, noted above
