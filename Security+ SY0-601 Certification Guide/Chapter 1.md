---
---
**CIA Triad**

![[./_resources/Chapter_1.resources/unknown_filename.png]]

* **Confidentiality**
	* Prevent disclosure of unauthorized data; ensure only authorized people have access to data
	* need-to-know
	* **encryption**
		* symmetric: uses one key (private or shared key)
		* asymmetric: uses two keys (private and a public key)
* **Integrity**
	* know the data has not been altered or tampered with
	* **hashing**: converts data into a numerical value called a hash or message digest
		* check the hash value against the original in order to ensure integrity; if the hash value changes you know the data has been tampered with
			* SHA1 (Secure Hash Algorithm 1): 160-bit
				* SHA2: 256-bit
				* SHA3: 512-bit
			* Message Direct Version 5 (MD5): 128-bit
				* MD5 is faster even though SHA1 is more secure
* **Availability**
	* ensure the data is always available
	* **resilience** improves availability
		* many choose the "cloud" because of this consistent availability and reliability
		* **Redundant Array of Independent Disks (RAID)** for data backup
		* **Heating Ventilation Air Conditioning (HVAC)** to regulate environments for critical systems
* **Examples of threats to parts of the triad**
	* employee stealing and selling company intellectual property - confidentiality
	* an employee deleting a database and backups because they were fired - availability
	* an employee programming a backdoor into a program in order to steal secrets - integrity and confidentiality
	* an employee downloading sensitive files from another's computer for purpose of blackmail - confidentiality
	* an employee accidentally deleting files, then changing logs to hide their mistake - integrity and availability
	* an employee not reporting a vulnerability to management in order to avoid working to fix it - potentially the whole triad depending on the vuln
	* an employee using software improperly and causing it to fall into an unknown state - potentially all three aspects
	* someone accidentally deleting files - availability
	* software or a network being misconfigured in a way that produces vulnerabilities - potentially the whole triad
	* an employee pointing vulnerability testing software at one's own system, crashing it - availability - and/or polluting the database - integrity

**Least Privilege** : give someone the least amount of access required to perform a task; need-to-know

*     if someone does take over an account or access improper information, they have few places to go
	* **example:** someone who had global access to a database - and could destroy the whole thing - now only has partial access

**Defense in Depth Model:**

* protecting data with a series of layers where if one fails another will be there to stop an attack
* ![[./_resources/Chapter_1.resources/unknown_filename.1.png]]
* **Examples**
	* **when creating software**
		* having security reqs, performing threat modeling, using secure design concepts and secure coding tactics, security testing
	* **network security**
		* turning on monitoring, having a **SIEM - Security Information and Event Managment (a dashboard for viewing potential security events in real time)** - having **IPS/IDS (Intrusion Prevention/Detection System)** and firewalls
	* **physical security**
		* locks, gates, fences, guards, etc.

**Security by Obscurity**

* if something is hidden, such as source code, it is less likely to be noticed
	* **obfuscation** - make something harder to read or understand.  some companies will obfuscate source code so it can't be reverse engineered
		* companies exist that can obfuscate code for you

**Attack Surface Reduction**

* **every** part of your application can be attacked, so the smaller the application the smaller the attack surface
	* remove anything that is not required

**Hard Coding**

* certain values are coded explicitly, so anyone with access to the code would have access to those values (passwords, etc.)

**Never Trust, Always Verify**

* never trust anything outside your own application
	* verify all outside data coming into your own application
	* consistently authenticate users - **session management**
	* ![[./_resources/Chapter_1.resources/unknown_filename.2.png]]

**Usable Security**

* find a way to make the secure option the easy option

**Factors of Authentication**

* a factor of authentication involves proving who you are to a computer
* **something you have**
* **something you are**
* **something you know**
* **Multi-factor authentication**
	* entering a username/password and then needing some second device or token to authenticate
	* username and password, then using a thumb print
* **not multi-factor**
	* username and password
	* username and password, then a security question (which are easy to break)
	

**Comparing Control Types**

* **Managerial Controls**
	* written by managers to reduce risks in an organization; incorporate regulatory frameworks so orgs are legally compliant
	* **annual risk assessment:**
		* directors look at org  infrastructure to see the risks imposed; risks can become greater or worse depending on technological change
	* **penetration testing/vulnerability scanning**
		* scanning is not intrusive as it only checks for vulnerabilities, while penetration testing is designed to exploit vulnerabilities
* **Operational Controls**
	* operations carried out day to day
		* **security awareness training**
		* **change management**
			* a policy to ensure that changes don't cause security risks; a **change advisory board** helps to ensure changes are well prioritized
		* **business continuity plan**
			* this is the contingency plan to keep an org up and running in case of a disaster; points of failure need to be identified
* **Technical Controls**
	* implemented by the IT team to reduce risks to the business
	* **firewall rules**: prevent unauthorized access via the network
	* **antivirus/antimalware**:  one of the most common threats to businesses; ensure these systems are up to date
	* **screen savers:** prevent access while a computer is idle
	* **screen filters:** prevent people around you from seeing your screen
	* **Intrusion Prevention Systems (IPS)/Intrusion Detection Systems (IDS): IDS** monitors the network for changes and the IPS stops attacks; and IPS can do the same duties as an IDS
* **Deterrent Controls**
	* things like cameras and motion sensors
* **Detective Controls**
	* used to investigate an incident
	* **CCTV:** records an incident that may need investigation
	* **Log files**: text files that record events and when they happened; they can let you see trends over a period of time
		* these can be stored in **Write Once Read Many (WORM)** drives so they can be read but not tampered with
* **Corrective Controls**
	* such as fire suppression; used to recover from an incident
* **Compensating Controls**
	* also called alternative or secondary controls
	* can be used instead of a primary control that has failed or is not available
	* an example can be using a username/password combo when someone forgets an access keycard
* **Preventative Controls**
	* put in place to deter attacks
		* disabling user accounts when someone leaves the company
		* harden operating systems
* **Access Controls**
	* identification
	* authentication
	* authorization

* **Discretionary Access Controls**
	* involves **New Technology File System (NTFS)** file permissions, where the user is only given the access they need to perform a job; also referred to as **user-based** or **user-centric**
		* full control
		* modify
		* read and execute
		* list folder contents
		* read
		* write
		* special permissions
		* data creator/owner
* **Mandatory Access Control (MAC)**
	* based on the government classification level of data
		* **top secret**: grave damage
		* **secret**: causes serious damage
		* **confidential**: causes damage
		* **restricted**: undesirable affects
		* **MAC roles**
			* **owner**: the person who writes the data and the only person who can determine classification
			* **steward**: person responsible for labeling the data
			* **custodian**: person who stores and manages classified data
			* **security administrator**: person who gives access to classified data once clearance is approved
* **Role-based Access Control**
	* a subset of a department carrying out a subset of duties
	* permits access based on the user's role in the org
		* users in accounting have no access to the information in sales
	* this can help designating individual permissions easier
* **Rule-based Access Control (RBAC)**
	* such as only allowing certain people access around certain times
* **Attribute-Based Access Control**
	* access restricted based on an attribute in the account
* **Group based access control**
	* people may be put into groups to simplify access, such as when multiple people need access to certain data.  First, these people are put in an IT group, and then that IT group is given access to data

**Linux Based Access Control**

* **Linux File Permissions (not SELinux)**
	* **Permission**
		* owner: first number
		* group: second number
		* all other users: third number
	* **Numerical values**
		* **4:** read
		* **2**: write
		* **1**: execute
			* **Examples:**
				* **764 access** means
					* **Owner**: read, write, execute (6)
					* **Group**: Read and write
					* **All other users**: Read
				* **R**: Read
				* **W**: Write
				* **X**: Execute
			* **a. Owner Full Control:** rwx --- ---
			* **b. Group Full Control:** --- rwx ---
			* **c. User Full Control:** --- --- rwx
				* Example:
					* rwx rwx rw- translates to the owner and group having read/write/execute privileges while all other users have read/write priv's

**Physical Security Controls**

* **Perimeter Security**
	* **Signage**: highly visible signs should alert people that they are entering a secure area
* **Fences/Gates**: open areas are more vulnerable to attackers; there are a variety of ways to control access to a gate; bollards can be installed to stop cars from running through the gate
* **Access Controls**: Armed guards can check the ID of those entering, and an access control list controlled by an internal deptartment
* **Lighting**: ensure everyone entering/exiting can be seen and make sure premises are safe
* **Cameras**: used to detect motion and other people/objects
* **robot sentries**: can be set up to patrol perimeters; they can sound alters and (why the fuck not) be armed
* **Industrial camo:** obscure high value targets from being viewed

**Building Security**

* **Security Guards:** using an access control list, check the identity cards of those entering the building
* **Two-person integrity/control**:  ensure that if one person is occupied at a desk that there is someone else maintaining security
* **Badges:** Visitors sign the visitor book and are allocated a badge indicating they are a visitor and not an employee; the badge should clearly identify the visitor and be displayed at all times
* **Key management:** departmental keys are signed out and signed back in to prevent someone from copying them
* **mantraps:** device that only allows one person to enter at a time
* **proximity cards:** contactless devices where a smart card is put near the proxmity sensor to gain access to a location
* **tokens:** small devices which can be touched to a proximity sensor to gain access to an area; the token may have a button to press or display a code to be entered
* **biometric locks:** use credentials that are unique to each person
* **electronic locks:** no physical key is needed to access an area but only a PIN; can be set to fail open in case of power outages or fail safe (door locked)
* **burglar alarms:** triggers alarms when intruders are detected
* **fire alarms/smoke detectors**
* **internal protection:** such as designated safe/secure areas; screen protectors
* **conduits:** conduits/cable distribution protects cables from unwanted damage
* **environmental controls:** HVAC/fire supression

**Device Protection**

* cable locks
* air gap
	* a computer is taken off the network and has no cable or wireless connection; this is to better ensure no data is stolen
* laptop safe
* USB data blocker
* vault
	* where data can be encrypted and stored in the cloud; an extra-secure story
* faraday cage
	* metal mesh structure preventing wireless communication from working from within the structure;

**Incident Response**

* how an organization responds to a cyberattack
* ideally, orgs would have a designated response team and written response policies
	* will learn from cyberattacks to better harden their networks
	* CSIRT - Computer Security Incident Response Teams
* NIST has a guide for various stages of effective incident response

* **Preparation**
	* know who to contact when an incident occurs and be able to contact each other
	* ensure **security information and event management system (SIEM)** are up and running properly
	* ensure there is documentation for all the hardware and software the org uses
* **Detection and Analysis**
	* the detection systems in the previous step should see any intrusion or anomaly 
* **containment, Eradication, and Recovery**
	* contain or destroy the breach, virus, etc.
		* with containment, admins can shut down certain systems and/or send the attack to a sandbox or honeypot
			* a sandbox is a separate environment which allows software to run without affecting the rest of the system
			* a honeypot is meant to attract hackers so as to draw their attention away from more vulnerable portions of the system
	* evidence regarding the attack needs to be gathered, such as logs of IP addresses, etc.
	* malicious files or applications need to be destroyed
* **Post-Incident Activity**
	* a breakdown of how the incident occurred and how to prevent another needs to happen

**Malware**

* malware is any sort of malicious software
* using malware is likely part of a pentesters work in one form or another
	* research the malware within a sandbox
* **Viruses**
	* programs that **replicate by infecting a file or multiple files, then copying themselves onto other computers** **via a network or physical media**
	* networks are the most common ways in which viruses spread
* **Worms**
	* worms don't need to alter other files to spread **but are self contained** and can spread through networks or physical media
* **Fileless Malware**
	* while there is a file (data) involved, fileless malware does not write to a target's data storage, but only uses the memory of the target
		* because the malware isn't a file on the hard drive, malware scans can miss it
	* starts by infecting an operating system process on the target
	* detected by observing the behavior on an infected machine
* **Ransomware**
	* encrypts files on a target machine, only decrypting them when a ransom is paid
* **Cryptominers**
	* use the processing power of computers to mind cryptocurrency
* **Botnets**
	* group of computers infected with malware that allows an attacker to control them
	* members of the botnet are coordinated to attack targets, often a DDoS attack
* **Spyware**
	* malware that threatens someone's confidentiality by showing an attacker some or all of the data on a machine
* **Trojans**
	* file or application that appears to the user as something else
* **Rootkits**
	* acquire unauthorized administrator access to a local machine and try very hart to evade detection
* **Modular Malware**
	* consists of multiple modules that each perform a different function
	* the first component will infect a machine and establish a connection with the attacker's **command and control servers**
		* these servers will eventually download different modules with other capabilities
* **Advanced Persistent Threats (APTs)**
	* a targeted cyberattack that can stay active on a computer for months or years
	* often very sophisticated and with the backing of large organizations like nation states, corporations, and organized crime

**Cyber Kill Chain**

* concept originates with kinetic warefare
* identify a target, dispatching appropriate attackers, figuring out how to attack effectively according to the context of the attack, and completing the attack
* **F2T2EA**
	* Find - identify a target
	* Fix - acquire precise location of the target
	* Track - monitor the target
	* Target - find the appropriate ways to attack the target
	* Engage - strike
	* Assess - evaluate how the attack went and gather intelligence
* the modern killchain is composed of
	* **Reconnaissance** - the attacker researches their target to assess vulnerabilities
		* harvest emails, stalk via social media, look for internet servers
	* **Weaponization** - malware is developed or bought that exploits the vulnerabilities discovered during reconnaissance 
	* **Delivery**
		* delivered to the target in any number of ways
			* physical media
			* phishing
			* watering holes - website a target often visits which are then compromised
	* **Exploitation** - malware starts working
	* **Installation** - malware installs whatever backdoors or modules it needs
	* **Command and Control**  - the attacker uses whaterver the malware installed in the previous phase to take control of the target, such as through a remote shell
	* **Actions and Objectives** - the attacker is now able to fully pursue their objectives

**Common Vulnerabilities and Exposure**

* it can be a pain in the ass to get executives on down to take security seriously and invest in what is needed; sometimes people just fuck up
* Know vulns are recorded in the **Common Vulnerabilities and Exposure System (CVE System)**
	*  a researcher may be asked if they've contributed to the CVE

**Phishing and Social Engineering**

* social engineering is essentially just fooling people into giving you access to sensitive information
* phishing is when an attacker pretends to be an entity a user trusts in order to get sensitive info such as bank information, etc.
	*  a fake website will be created and an email sent to a target; the target then clicks a link in the email and is redirected to the malicous website
	* **spear phishing**  is the same above tactic used on a specific target

**Airgapped machines**

* a machine that is isolated from other networks or only connected to very secure networks
* physical media would be needed to attack an airgapped machine
* likely within a secure and controlled space
* obscure ways of observing machine behavior have been used to attack airgapped machines
	* seeing how a harddrive blinked

**Dark Web**

* the dark web is just the part of the internet that isn't indexed by search engines
* many tools exist to make navigating the dark web easier
	* TOR
		* The Onion Router
	* I2P
		* Invisible Internet Project
* distinguished from the **clearnet**
	* on the clearnet - the normal internet - your internet traffic can be traced via your IP address along all the paths and servers it's crossed
	* on TOR and I2P, each node you access to get to  your destination has a proxy server with a different IP address, so tracing your activity will only go so far as the nearest  node
* websites that can only be access via TOR or I2P will end with **.tor** or **.i2p** domains

**Understanding Digital Forensics**

![[./_resources/Chapter_1.resources/unknown_filename.3.png]]

* **Collection**
	* data is examined, extracted from devices, and converted into formats that could be analyzed
* **Examination**
	* before any examination, data is hashed, then the investigation will be carried out by the proper forensic tool
	* after examination, the data is hashed again as a way to ensure the examination tools haven't interfered with the data
		* a medium that only allows read-only access to data could be used
* **Analysis**
	* when all the data has been collected, it's analyzed and then transformed into information that cna be used as evidence
* **Reporting**
	* a report is compiled that can be used as evidence
* **Admissibility**
	* all evidence relevant to the case is deemed admissible only if it is relevant to the disputed facts of the case and does not violate any laws or legal statutes
* **Order of Volatility**
	* preserve the most perishable items first
		* do not try and stop the attack until we have secured the volatile evidence to better identify the source
			* **web-based attack**: the security team is trying to to capture the network traffic to find the source of the attack, as this is the most volatile evidence
			* **attack inside the computer**: evidence is captured in order of what is most volatile
				* CPU cache - fast block of volatile memory used by the CPU
				* RAM - the volatile memory used to run applications
				* Swap/page File/Virtual Memory - used for running applications when RAM is totally exhaused
				* Hard Drive - data at rest for storing data
			* **removable storage drive attached to a computer/server**
				* when a USB drive is plugged in, programs are run in RAM, so this volatile memory would need to be captured
			* **Command line tools**
				* learn which command line tools provide information that would disappear if you reboot the computer - **netstat.**  with **netstat -an** the listening and established ports are shown, info that would be lost if the computer were rebooted

* **Collection of Evidence**
	* **E-discovery**
		* when companies may be subpoenaed so tech folks can collect, review, and interpret electronic documents located on hard disk and other forms of storage
	* **chain of custody**
		* chain of custody is crucial
		* starts when the evidence has been collected, bagged, tied, and tagged to ensure the evidence has not been tampered with
		* lists the evidence and who has handled it along the way
			* **examples**
				* **missing entry on chain of custody document -** a chain of custody regarding laptops my result when there is no formal handover between parties
				* **evidence leaves someone's possession -** because certain evidence is not in one's possession at all times the chain of custody is broken
	* **provenance**
		* when the chain of custody is intact and there is no tampering of evidence, this is **data provenance**
	* **legal hold**
		* process of protecting any documents that can be used in evidence from being altered or destroyed; also known as **litigation hold**
		* **examples**
			* a person's email box is placed on **legal hold**, so the limit on the mailbox is lifted, and message can still be sent/received, but not deleted; so the person under investigation isn't alerted they are under investigation
		* **data acquisition**
			* process of collecting all evidence from devices, paper format, letters, bank statements, etc.
				* first collect all volatile evidence
				* data must be tagged and bagged and included in the evidence log
		* **artifacts**
			* log files, registry hives, DNA, fingerprints, or fibers of clothing
		* **time offset**
			* record the time offset
			* the regional time, so if the investigation crosses timezones the time can be **normalized**
			* **time normalization**
				* when evidence is collected across multiple timezones it is put into a common format, such as GMT, so as to better be put into a meaningful sequence
		* **time stamps**
			* when files were created and modified and accessed 
		* **forensic copies**
			* make a forensic copy to keep the original data intact for analysis
			* data should be hashed from beginning to end to ensure it's not been tampered with
		* **capturing system images**
			* a system image is taken and hashed to ensure integrity
		* **firmware**
			* also called embeded systems, could be reversed engineered by an attacker
			* compare the original firmware code with what is currently on system
		* **snapshots of virtual machines**
			* a snapshot of a virtual machine can be exported to be studied later
		* **screenshot**
			* take screenshots of applications or viruses
		* **taking hashes**
			* forensic copies should be hashed, then re-hashed to ensure data integrity
		* **network traffic logs**
			* first capture volatile network traffic before trying to stop the attack
			* a Security Information Event Management (SIEM) system  can help collect these entries
			* a computer with a  rapidly expanding virus should be removed before trying to collect network traffic
		* **preservation**
			* you can preserve files in a WORM drive; you cannot delete data from a WORM drive

* **Cloud Forensics**
	* Cloud Forensic Process 26
		* Stage A - verify the purpose of cloud forensics
		* Stage B - verify the cloud service
		* Stage C - Verify the type of technology used behind the cloud
		* Stage D - verify teh role of the user and talk with the **Cloud Service Provider (CSP)** to collect the evidence required
	* Right to Audit Clauses
		* these allow someone to go on premises to inspect books and records
	* Jurisdiction
		* US. CLOUD ACT in 2018 to get Microsoft data held in Ireleand
		* **General Data Protection Regulation (GDPR)** in the EU
	* Data Breach Notification
		* fines up to 10 million euros
		* under GDPR companies must notify of breaches within 72 hours

**REVIEW QUESTIONS**

1\. What are the three components of the CIA triad?

2\. Why might a CCTV camera be situated outside a building without any film inside?

3\. What does confidentiality mean?

4\. How can we control access of personnel to a data center?

5\. What is the purpose of an air gap?

6\. Name three main control categories.

7\. Name three physical controls.

8\. Following an incident, what type of control will be used when researching how the

incident happened?

9\. How do I know whether the integrity of my data is intact?

10\. What is a corrective control?

11\. What type of control is it when you change the firewall rules?

12\. What is used to log in to a system that works in conjunction with a PIN?

13\. What is the name of the person who looks after classified data and who is the

person that gives people access to the classified data?

14\. When you use a DAC model for access, who determines who gains access to

the data?

15\. What is least privilege?

16\. What is the Linux permission of 764? What access does it give you?

17\. The sales team are allowed to log in to the company system between 9 a.m. and

10 p.m. What type of access control is being used?

18\. Two people from the finance team are only allowed to authorize the payment

of checks; what type of access control are they using?

19\. What is the purpose of the defense in depth model?

20\. When someone leaves the company, what is the first thing we should do with their

user account?

21\. What do US companies that host websites in the US have to comply with

if customers are based in Poland?

22\. How can a company discover that their suppliers are using inferior products?

23\. What is one of the most important factors between someone being arrested and

their appearance before the judge in court?

24\. Can you explain what the purpose of the CLOUD Act and COPOA is?

25\. What is Stage C of Cloud Forensic Process 26?
