---
source: https://tryhackme.com/room/furthernmap
---
an example of a good thorough scan would be **nmap -T4 -A -p- \[ip address\]**

When port scanning with Nmap, there are three basic scan types. These are:

* TCP Connect Scans (\-sT)
* SYN "Half-open" Scans (\-sS)
* UDP Scans (\-sU)

Additionally there are several less common port scan types, some of which we will also cover (albeit in less detail). These are:

* TCP Null Scans (\-sN)
* TCP FIN Scans (\-sF)
* TCP Xmas Scans (\-sX)

Most of these (with the exception of UDP scans) are used for very similar purposes, however, the way that they work differs between each scan. This means that, whilst one of the first three scans are likely to be your go-to in most situations, it's worth bearing in mind that other scan types exist.
In terms of network scanning, we will also look briefly at ICMP (or "ping") scanning.

**TCP Connect Scan**

this scan is initiated with the **\-sT** flag

this scan works by performing the TCP three way handshake with each target port; this allows nmap to see if the destination is open based on the response it sends

For example, if a port is closed, [RFC 793](https://tools.ietf.org/html/rfc793) states that:
_"... If the connection does not exist (CLOSED) then a reset is sent in response to any incoming segment except another reset.  In particular, SYNs addressed to a non-existent connection are rejected by this means."_

so, if nmap sends a tcp request with the SYN flag to a closed port, the target will  respond with the **RST (Reset) flag**, thus allowing nmap to figure out the given port is closed:

![[./_resources/Nmap.resources/STN-RST response.png]]
if the given port is open, then it will respond normally with the SYN/ACK flags, thus showing itself to be open

**What if the port is hidden behind a firewall?**

Many firewalls are configured to drop incoming packets; nmap sends TCP SYN request and will receive nothing back.  The latter implies the port is being protected by a firewall and is considered **filtered.**

 In Linux, you can set the firewall to respond with an RST packet using  iptables -I INPUT -p tcp --dport <port> -j REJECT --reject-with tcp-reset

The above setting will make getting an accurate reading of a target computer difficult

**SYN SCANS**

SYN scans - **sS** - scan the TCP port range of a target(s) - these scans work differently, though.  SYN scans can be referred to as 'half-open' or 'stealth' scans

After the full three-way handshake SYN scans send back an RST TCP packet (to prevent the server from repeatedly trying to make the same request)

Here is the sequence:

![[./_resources/Nmap.resources/SYN scan example.png]]
![[./_resources/Nmap.resources/SYN scan console.png]]

**Advantages** to SYN scans:

* can bypass older Intrusion detection systems as the latter look for a three-way handshake
* SYN scans are often not logged by applications listening on open ports, as the practice is to log only fully-established connections
* SYN scans are faster as they don't require a completed connection

**Disadvantages** to SYN scans

* usually to work correctly they require sudo permissions, due to the ability to create raw packets (vs a full TCP handshake) is a privilege only the root user has 
* a SYN scan may take down an unstable system 

Given that the **advantages outweigh the disadvantages** SYN scans are the default scans of NMAP **if run** **with** **sudo permissions.**  without sudo permissions Nmap defaults to TCP Connect

the same rules for identifying closed and filtered ports apply

**UDP Scans**

Unlike TCP scans, UDP scans are **stateless**; meaning that rather than have a type of two-way handshake UDP just launches its packets and hopes for the best.  this trait of UDP allows it to prioritize speed over quality (such as streaming data), but i makes scanning UDP connects much slower as there is no handshake.  The Nmap switch for scanning UPD is **\-sU**.   Nmap will send just raw UDP packets - empty requests.  That being said, if a port is occupied by a well-known service, Nmap will send a protocol-specific payload which is more likely to get a response we're able to get useful results from.

there should be no response when sending packets to a UDP port, so Nmap will consider the port **open|filtered.**  This means while the port is open, it may be firewalled.  If a response does happen to come back, the port is marked as **open.**  A second packet will be sent to double-check the port and if there still is no response Nmap will consider it open|filtered.

If a UDP port is **closed**, the target should respond with an **ICMP (ping)** packet containing the message that the port is unreachable.  this allows ports to be clearly identified, but is a slow process:  you're sending at least two packets to every port to see if it is at least open. It can take approximately 20 minutes to scan 1000 ports. Because of this, you want to run **\--top-ports <number>** enabled (where <number> is the number of most commonly used UDP ports)

**NULL, FIN, Xmas**

These are interlinked scans that are more rarely used than the SYN stealth scan

* **NULL (-sN)** is when the TCP request is sent with  no flags set; if the host is closed then it should respond with an RST
	* ![[./_resources/Nmap.resources/unknown_filename.png]]
* **FIN (-sF)** work almost identically to NULL except there is a FIN flag sent to close an active connection; again and RST response is sent if the port is closed
	* ![[./_resources/Nmap.resources/unknown_filename.1.png]]
* Xmas (-sX) sends a malformed TCP packet and expects and RST from any closed ports
	* the name comes from the appearance of the flags it sets (PSH, URG, FIN) which looks like a xmas tree
	* ![[./_resources/Nmap.resources/unknown_filename.2.png]]

All these types of scans act the same when encountering open ports, and in the same way as a UDP scan.  if the port is open there will be no response to the malformed packet, but will also be true if the port is protected via firewall.  so, NULL, FIN, and Xmas will only identify ports as open|filtered, closed, or filtered

Windows and some CISCO devices will response with and RST packet when seeing any malformed packet regardless if the port is actually open or not.  **All we want to do with these three types of scans is evade firewalls**.  most firewall are configured to send incoming TCP packets  to blocked ports which have a SYN flag set - this blocks any new connection initiation requests.  When sending requests that don't have a SYN flag set, the above sort of firewall is effectively bypassed. (Modern well-configured firewalls don't only rely on this fact, though.)

**ICMP Network Scanning**

initially, the network we're targeting is going to be a black box.  so, we first need to get a **map** of the networks structure, meaning we need to ascertain which IP addresses contain active hosts and which don't.  Nmap can do a **ping sweep** to get a  look at the whole network; this involves Nmap sending ICMP packets to each possible IP address on the system on the network, recording which IP addresses respond as being alive (this is not always accurate but it gives a good baseline).

We do this ping sweep with the **\-sn** switch along with the range of IP addresses with either a hyphen or **CIDR** notation: 

* nmap -sn 192.168.0.1-254
* nmap -sn 192.168.0.0/24

How would you perform a ping sweep on the 172.16.x.x network (Netmask: 255.255.0.0) using Nmap? (CIDR notation) == nmap -sn 172.16.0.0/16
