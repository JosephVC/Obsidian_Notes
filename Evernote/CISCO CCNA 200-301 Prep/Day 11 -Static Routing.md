---
---
![[./_resources/Day_11_-Static_Routing.resources/image.png]]

* the **connected route** = the network the interface is connected to
* **local route** \= the actual IP address on the interface (with a /32 mask)
* the **gateway** on a machine - such as PC1 or PC4 in the above picture - is the address where the machine will forward packets destined for a location outside the local network
* the **default gateway** is known as the **gateway of last resort**

**Configure a Default Route**

* to configure the **gateway of last resort** on a Cisco router, you must configure a **default route**
	* a **default route** is a route that matches ALL possible destinations
* it is used only if a more specific route match isn't  found in the routing table
* the default route is the **least** specific route possible
	* IP: 0.0.0.0
	* subnet mask: 0.0.0.0
	* so to set a default route/gateway of last resort, configure the route to 0.0.0.0/0
		* there is no fixed portion of this address; no portion of this address that can't change, **so this covers a huge range of possible addresses**
			* the **0.0.0.0/0** actually covers a range of IP addresses from 0.0.0.0 -> 255.255.255.255

**Configuring a Static Route**

* a **static route** is  a route you configure yourself
	* contrast this with **connected/local** routes which are automatically added to the routing table
* the command to configure a static route is \`ip route \[some destination address\] \[the mask\] \[the next hop\]
	* ![[./_resources/Day_11_-Static_Routing.resources/image.1.png]]

* **switches** flood frames with unknown destinations (destinations not in the MAC address)
* **routers** drop packets with unknown destinations

**Configuring a Default Route**

* use the command `ip route [the destination] [the mask] [exit interface]`
* ![[./_resources/Day_11_-Static_Routing.resources/image.2.png]]

**Most Specific Matching Route**

* when a router looks up an address in its routing table, it look for the **most specific matching route**
* **most specific** \= longest prefix length (/32 > /24 > /16 > /8 > /0)
* ![[./_resources/Day_11_-Static_Routing.resources/image.3.png]]
	* the router will choose the most specific address it can, so it will look for an address with a longer prefix length rather than one with a smaller prefix and more zeros in the address
	* **code 'C'** in the above routing table stands for **connected**
	* **code 'L'** in the above routing table stands for **local**
	* **code 'S'** the above routing table stands for **static**
	* **code '\*'** stands for **candidate default**

**QUIZ**

1. The IP address configured on a routing interface will appear in the routing table as what kind of route?
	* local route
		* **local** addresses use a /32 mask, which specifies the exact address configured on the interface
		* **connected** addresses represent the network the local address is part of
		* **static** address are manually configured addresses, unlike connected and local addresses which are automatically added when you configure an IP address on an interface and enable it
		* **internal** is not a type of route you can find in a routing table

2. Which command configures a default route on a Cisco Router?
	* `ip route destination-address mask next-hop`
	* 0.0.0.0  0.0.0.0  10.1.1.254
		* the above destination address and mask matches all routes

3. Which is an accurate statement about the behavior  of routers and switches?
	* **routers drop packets** with an unknown destination IP address while **switches flood frames** with an unknown destination MAC address
		* you can configure a gateway of last resort on a router, telling the router where to forward packets that don't match anything else in the routing table

4. Which two types of addresses are automatically added to the routing table when you configure an IP address on an interface and enable it?
	* connected and local

5. ![[./_resources/Day_11_-Static_Routing.resources/image.4.png]]
