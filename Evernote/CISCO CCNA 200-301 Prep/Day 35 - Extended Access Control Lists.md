---
---
**Configuring numbered ACLs with subcommands**

![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.png]]

**Advantages of named ACL config mode**

* you can easily delete individual entries in the ACL with `no [entry number]`
	* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.1.png]]
	* when configuring numbered ACLs from global config mode, **you can't delete individual entries, you can only delete the entire ACL**

* you can insert new entries in between other entries by specifying the sequence number
	* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.2.png]]

**Resequencing ACLs**

* there is a **sequencing** function that helps edit ACLs
* the command `ip access-list resequence [acl-id starting-seq-num increment]`
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.3.png]]

**Extended ACLs**

* Extended ACLs function mostly the same as standard ACLs
* they can be numbered or named, just like standard ACLs
	* numbered ACLs use the following ranges: 100 - 199, 2000 - 2699
* they are processed from top to bottom, just like standard ACLs
* However, they can match traffic based on more parameters, so they are more precise (and more complex) than standard ACLs
* the command to configure an extended numbered ACL from global config mode `access-list` _`number`_ `[permit | deny ]` _`protocol src-ip dest-ip`_
	* for an extended named ACL:
		* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.4.png]]

**Matching the protocol**

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.5.png]]

**Matching the source/destination IP address**

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.6.png]]
	

![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.7.png]]

**Matching the TCP/UDP port numbers**

* when matching TCP/UDP, you can optionally specify the source and/or destination port
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.8.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.9.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.10.png]]

**Extended ACLs**

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.11.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.12.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.13.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.14.png]]
* checking which ACLs are applied to an interface
	* `show ip interface --interface name--`

**QUIZ**

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.15.png]]
* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.16.png]]
	* b

![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.17.png]]

* c)
	* after the command `ip access-list resequence` you must specify the name, new sequence number, and the number the sequencing will increment by
		* the answer for C) tells the router than the new entry will be 5 and will increment by 10

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.18.png]]
	* ACL 112
		* the first entry denies protocol number 89, which is OSPF
		* `permit ip any any` allows other packets
		* then g0/2 is specified, and the rule is applied to outbound traffic

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.19.png]]
	* c, e
		* we are trying to filter traffic going into the g0/1 interface, which is why we apply the rule **inbound** on g0/1

* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.20.png]]
	* ![[./_resources/Day_35_-_Extended_Access_Control_Lists.resources/image.21.png]]
