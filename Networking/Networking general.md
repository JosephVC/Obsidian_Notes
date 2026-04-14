
- backplane - basic circuitry that provides connectivity between the different modules on a switching or routing device
	- https://www.auvik.com/franklyit/blog/backplane-throughput/
	- if you have a switch with several multiport modules installed, the data bus those modules plug into are the backplane
	- the backplane is the foundational wiring and configuration that other things require 
	- **active backplane** include some computing power on the backplane
	- **passive backplane** are just plain physical connectors
	- the term backplane is used interchangeably with the term **switch fabric**
		- the switch fabric is the network topology a backplane would use
	- backplane capacity/bandwidth is very important
		- this bandwidth is the cap on network device's throughput
		- if the backplane capacity is 10Gbps you could not have 24 devices running at 1Gbps speed as that would be more than double the throughput the backplane would allow
	- while a motherboard  could be thought of as a type of backplane, it is the backplane for a single device with a limited number of slots. a proper backplane will have a large - 20 - number of slots for expansion to assemble a system with a lot of options
	- **Interface throughput vs backplane throughput**

https://www.auvik.com/franklyit/blog/network-throughput-vs-bandwidth/

https://www.auvik.com/franklyit/blog/backplane-throughput/