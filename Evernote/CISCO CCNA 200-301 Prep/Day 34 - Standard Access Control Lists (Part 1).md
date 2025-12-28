---
---
**Access Control Lists (ACL)**

* control who has access to different parts of the network
* ACLs function as a packet filter, allowing the router to admin or discard certain packets
* ACLs can filter traffic based on source/destination IP addresses, source/destination ports

**How ACLs Work**
![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.png]]

* ACLs are configured on a router
	* global config mode
* they are ordered entries of **ACEs (Access Control Entries)**
	* **the order of these entries if very important**
	* when the router checks a packet against an ACL, it processes the ACEs in order, from top to bottom
* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.1.png]]
* if the packet matches one of the ACEs in the ACL, the router will take the specified action and stop processing the packet.  all other entries below the matching entry will be ignored
* **a maximum of \*one\* ACL can be applied to a single interface \*per direction\***
* ACLs must be applied to an interface
	* either inbound or outbound
* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.2.png]]

**Implicit Deny**

* What will happen if a packet doesn't match any entries in the ACL?
* there is an implicit deny at the end of all ACLs
* the implicit deny tells the router to deny all traffic that doesn't match any of the configured entries in the ACL
* you should be aware of this implicit deny so you don't deny traffic that you meant to receive

**ACL Types**

* **Standard ACLs** - Match based on **Source IP address _only_**
	* Standard Numbered ACLs
		* identified with a number ACL 1, ACL 2, etc.
		* different types of ACLs have a different range of number that can be used
			* 1-99, 1300-1999 is the standard range for standard numbered ACLs
			* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.3.png]]
		* `access-list [some number] {deny | permit } [some ip wildcard mask]`
			* do not try to use a standard subnet mask when configuring ACLs
			* the below are all different ways of configuring an ACL which have the same result
				* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.4.png]]
					
				* the bottom two are good for /32 networks, but for a /24 network you'll need to use the 0.0.0.255 mask
				* `permit  any` tells the router to admit all traffic, from any IP
					* `permit 0.0.0.0 255.255.255.255` would accomplish the same
		* you can make comments/remarks when configuring ACLs with the `remark` keyword (NOTE:  you don't need the hash symbols, unless you want to draw specific emphasis on your comment)
			* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.5.png]]
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.6.png]]

* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.7.png]]
	

* Standard Named ACLs
	* match traffic based solely on the source IP of the packet
	* identified with a name - PERMIT\_FOO
	* standard named ACLs are configured by entering **standard named ACL config mode** and then configuring each entry within that config mode
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.8.png]]
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.9.png]]
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.10.png]]
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.11.png]]
		* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.12.png]]

* **Extended ACLs** - match based on **Source/Destination IP and or port**
	* Extended number ACLs
	* Extended Named ACLs

**QUIZ**

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.13.png]]

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.14.png]]

* R2 g0/2
* outbound
	* standard ACLs should be applied as close to the destination as possible

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.15.png]]

* b
	* you can only have on ACL applied in each direction, and once an item in the ACL is met, all others below it are ignored

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.16.png]]

* d)
	* because the ACL was applied on R1s g0/0 interface, when the PCs try to ping server  2, R1 won't check the ACL as it sends them out of g0/0
	* when the reply from server 2 arrives on the g0/0 interface, it **will** check the ACL, but as the server's IP will be checked against the ACL, it will be permitted by the `permit any` at the end of the ACL

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.17.png]]

* C
	* because every ACL includes an **implicit deny** it will deny any packets that don't match any entries in the ACL

![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.18.png]]

* B)
	* ![[./_resources/Day_34_-_Standard_Access_Control_Lists_(Part_1).resources/image.19.png]]
		* "do not negate statements located lower in the ACL."
