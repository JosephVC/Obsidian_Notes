---
---
**DNS** (Domain Name System) is how a URL gets converted to an IP address.  the DNS servers are what find the particular IP address associated with google.com, etc., sending that IP address back to ur computer, and our computer then sends the request to that particular address

**Breaking the Request Process Down**

1.  When a request for a particular website is made, the computer first checks **local cache** to see if the IP address for the desired website isn't already stored.  If not, the computer moves on to the second step.
2. The computer sends a request to a **recursive DNS server.**  These should already be known to the router on one's network.  ISPs often have these servers, but larger orgs like Google and OpenDNS also have them. Because details of these recursive servers are stored in the router, the computer will automatically know where to send requests for information.  Recursive servers also maintain a cache of results for popular domains, but if the site requested isn't in the cache, the recursive server will pass the request to the **root name server.**
3. there are 13 root name servers in the world, and keep track of the DNS servers in the next level down, the **Top-Level Domain** servers.
4. the servers for the **Top-Level Domains are split up into extensions**, with certain servers handling the **.com** domains and others handling **.co.uk** domains.  These Top-Level Domain servers themselves also monitor the lower level **Authoritative name servers**, which handle requests handed them by the Top Level servers
5. the Authoritative servers store information for all domains directly.  So, every domain in the world will have a record on some Authoritative server, somewhere.  When a request sent by my computer is received by an Authoritative server, the latter will send back the appropriate IP back to me, allowing to access the appropriate webpage.

**The dig Command**

the format for dig is **dig \[domain\] @\[IP address of a DNS server\]** 

the most useful portion of the response is the **ANSWER** section, which among other things contains the **TTL (Time To Live)** information of a queried DNS record.  When a computer queries a domain name, it stores the results in local cache.  TTL tells the computer when to stop considering the given record as valid and obtain a fresh record by querying the data again.

The TTL is found in the second column of the ANSWER section, and **is measured in seconds.**
