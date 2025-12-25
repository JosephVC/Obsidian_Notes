---
---
**Signature-Based Detection**

* how most antivirus works
* based on attacks that have been seen before
* checks for byte pattern
	* found in files and processes, network packets
	* tougher with encrypted data
* signatures are comparatively simple and easy to use; efficient

**How Can Malware Avoid Detection**

* has no signature match (until the malware scanner has analyzed the signature and has updated the signature database)
* very complex
	* make it behave like a regular application
	* make it work slowly
	* the malware requires context and has multiple signatures

**Indicators of Compromise (IoC)**

* stop just looking for signatures, start looking for abnormal behavior
* some artifact has been left behind that malicious behavior has occurred
* some odd URL
* a new, unexpected file
* an odd file execution or process
* new or unexpected registry entries
* unexpected resource usage
* odd new applications or connections to new ports
* network signatures indicating a **RAT (Remote Access Tool)**
* new unexpected protocols
* new unexpected network devices
* new unexpected user behavior
* **IoCs: Shift in Perspective**
	* you can use automated tools - HIPS/HIDS (Host Based Intrusion Detection System/Prevention System) to better analyze
	* Correlation SIEM (Security Information Event Management)
		* one signature/IoC can be open to interpretation, but multiple incidents can be correlated
	* still tough to interpret a given computer event as good or bad

**Determining IoCs:  Reputation Method**

* has an incident ever been associated before with an attack
