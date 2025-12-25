---
---
![[./_resources/pfSense_not_loading_webConfigurator.resources/unknown_filename.png]]

* I can successfully ping the webConfigurator address, 172.16.1.1
* the above screen appears despite following directions to the letter
	* even tried changing the IP of the LAN to potentially get around issues
* tried running a **pkg update -f** and **pkg upgrade -f**  to see if that helps, will also restart the webConfigurator
	* this did not work
* also tried configuring the LAN adapter (host-only internet adapter) to automatic
	* ![[./_resources/pfSense_not_loading_webConfigurator.resources/unknown_filename.1.png]]
	* **this worked!**
	* will try switching the LAN address back to what the instructional book said earlier - 172.16.1.1
		* nope, this broke things again
		* will try a forum suggestion, which is switching the LAN to 192.168.2.1
			* **this works!**
