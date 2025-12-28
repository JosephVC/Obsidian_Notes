---
source: https://comptiacdn.azureedge.net/webcontent/docs/default-source/exam-objectives/comptia-cysa-cs0-003-exam-objectives-(1-0)-(2)-(002).pdf?sfvrsn=354cd264_2
---
1.0 Security Operations

1.1 - Explain the importance of system and network architecture
concepts in security operations.
**• Log ingestion**

* Log ingestion is the process where log data from external sources like hosts, applications, and cloud-based monitoring services is formatted and updated
* ==it is important because==

    - Time synchronization

* time synchronization in terms of logging refers to synching the time stamp of the log with a reliable external time source, such as a reliable external NTP server
	* a collection of these NTPservers would be e here: <https://www.ntppool.org/en/>
* ==it is important because==

    - Logging levels

* logging levels classify log entries by urgency, which helps filter logs and control the information you see.
* ==it is important because==
* the most common severity levels of logging are: 
	* OFF
		* nothings gets logged
	* FATAL
		* implies a critical function cannot be completed or some other severe problem exists such as inability to connect to the network
	* ERROR
		* notes a non-catastrophic but important problem with the application
	* WARN
		* there is a problem with the application, but things seem to be running normally despite the error; the problem may or may not occur again, but you should keep an eye on things
	* INFO
		* state what is happening in the normal operation of the application
	* DEBUG
		* diagnostic information used to troubleshoot an issue
	* TRACE
		* more granular than DEBUG; can log what happens in the application itself as well as libraries used; can be used to look at the steps the application made
	* ALL
		* custom log level, effectively combining the other levels as desired

**• Operating system (OS) concepts**
    - Windows Registry

* a hierarchical database storing low-level information for the Windows OS and other applications that use the registry
* ==it is important because==

    - System hardening

* collection of tools and techniques to reduce vulnerability in systems
* it is important because reduce security risk by reducing potential attack vectors and condensing the system's attack surface
* everything from how applications interact to how networking operates is affected
* remove vulnerabilities such as
	* default passcodes
	* hardcoded passcodes or other credentials stored in a text file
	* unpatched software/firmware
	* weak or absent privileged access controls
	* poorly configured portions of system infrastructure - ports, BIOS, firewall, networking gear, etc.
	* weakly encrypted data or network traffic

    ==-== ==File structure==

* ==a collection of logically related entities==

    ==-Configuration file locations==
    ==-== ==System processes==
    ==-== ==Hardware architecture==
**• Infrastructure concepts**
    - Serverless

* allows devs to build services without concern for the underlying architecture
* often seen in cloud environments, where code can be deployed but servers are managed by others
* often relies on APIs
* ==it is important because==

    - Virtualization

* allows the running of one or several other operating systems in a virtualized environment on top of a host OS
* ==it is important because==

    - Containerization

* software deployment process that bundles an application's code with all the files and libraries it needs to run on any infrastructure
* rather than being stuck creating applications meant to run on a particular OS, you can create containers for that same application to run on any OS
* this allows for increased portability, scalability, fault tolerance, and agility
* ==it is important because==

**• Network architecture**
    - On-premises

* a software and/or a hardware infrastructure setup deployed and running from within the confines of your organization
* the org has complete control over the infrastructure
* ==it is important because==

    - Cloud

* resources are pooled via virtualization and then shared across a network
* ==it is important because==

    - Hybrid

* this is where portions of the IT infrastructure are in the cloud while others are on premise
* ==it is important because==

    - Network segmentation

* a network is divided into multiple segments/subnets, with each segment acting as its own network
* ==it is important because==
* admins have a greater control of information between subnets
* admins can set policies for individual subnets
	* valuable assets can be confined

    - Zero trust

* is defined in SP 800-207
* requires all users, inside our outside of the network, to be fully authenticated and authorized to access data and applications
* federal agencies must adhere to zero trust per executive order in 2021
* and is **important** because it creates a system where all access to assets are continuously vetted prior to allowing access
	* this can help prevent old credentials being used to access data/infrastructure
	* if an intruder/unauthorized person gains access, their 'blast radius' of influence is limited as other services will require their own verification
	* context collection and response are automated; data regarding credentials, logins, etc are easier to collect

    - Secure access secure edge (SASE)

* combines software defined wide area network (SD-WAN) with a variety of security capabilities
* pushes security and access closer to users by dynamically allowing or denying connections to applications or services
* rather than focus on data centers, the focus shifts to the identity of users and devices and the workflows and traffic patterns between them
* this is **important** because it takes into consideration modern ways of using a network rather than sticking with traditional patterns

    - Software-defined networking (SDN)
**• Identity and access management**
    - Multifactor authentication (MFA)
    - Single sign-on (SSO)
    - Federation
    - Privileged access management (PAM)
    - Passwordless
    - Cloud access security broker (CASB)
**• Encryption**
    - Public key infrastructure (PKI)
    - Secure sockets layer (SSL)
inspection
**• Sensitive data protection**
    - Data loss prevention (DLP)
    - Personally identifiable information (PII)
    - Cardholder data (CHD)

1.2 - Given a scenario, analyze indicators of potentially malicious activity.
**• Network-related**
    - Bandwidth consumption
    - Beaconing
    - Irregular peer-to-peer communication
    - Rogue devices on the network
    - Scans/sweeps
    - Unusual traffic spikes
    - Activity on unexpected ports
**• Host-related**
    - Processor consumption
    - Memory consumption
    - Drive capacity consumption
    - Unauthorized software
    - Malicious processes
    - Unauthorized changes
    - Unauthorized privileges
    - Data exfiltration
    - Abnormal OS process behavior
    - File system changes or anomalies
    - Registry changes or anomalies
    - Unauthorized scheduled tasks
**• Application-related**
    - Anomalous activity
    - Introduction of new accounts
    - Unexpected output
    - Unexpected outbound communication
    - Service interruption
    - Application logs
**• Other**
    - Social engineering attacks
    - Obfuscated links

1.3 - Given a scenario, use appropriate tools or techniques to
determine malicious activity.
**• Tools**
    - Packet capture
                o Wireshark
                o tcpdump
    - Log analysis/correlation
                o Security information and event management (SIEM)
                o Security orchestration, automation, and response (SOAR)
    - Endpoint security
                o Endpoint detection and response (EDR)
    - Domain name service (DNS) and Internet Protocol (IP) reputation
                o WHOIS
                o AbuseIPDB
    - File analysis
                o Strings
                o VirusTotal
    - Sandboxing
                o Joe Sandbox
                o Cuckoo Sandbox
**• Common techniques**
    - Pattern recognition
                o Command and control
    - Interpreting suspicious commands
    - Email analysis
                o Header
                o Impersonation
                o DomainKeys Identified Mail (DKIM)
                o Domain-based Message
         Authentication, Reporting, and Conformance (DMARC)
                o Sender Policy Framework (SPF)
                o Embedded links
    - File analysis
                o Hashing
    - User behavior analysis
                o Abnormal account activity
                o Impossible travel
**• Programming languages/scripting**
    - JavaScript Object Notation (JSON)
    - Extensible Markup Language (XML)
    - Python
    - PowerShell
    - Shell script
    - Regular expressions

1.4 - Compare and contrast threat-intelligence and threat-hunting
concepts.
**• Threat actors**
    - Advanced persistent threat (APT)
    - Hacktivists
    - Organized crime
    - Nation-state
    - Script kiddie
    - Insider threat
                o Intentional
                o Unintentional
    - Supply chain
**• Tactics, techniques, and procedures (TTP)**
**• Confidence levels**
    - Timeliness
    - Relevancy
    - Accuracy
**• Collection methods and sources**
    - Open source
                o Social media
                o Blogs/forums
                o Government bulletins
                o Computer emergency response team (CERT)
                o Cybersecurity incident response team (CSIRT)
                o Deep/dark web
    - Closed source
                o Paid feeds
                o Information sharing organizations
                o Internal sources
**• Threat intelligence sharing**
    - Incident response
    - Vulnerability management
    - Risk management
    - Security engineering
    - Detection and monitoring
**• Threat hunting**
    - Indicators of compromise (IoC)
                o Collection
                o Analysis
                o Application
    - Focus areas
                o Configurations/misconfigurations
                o Isolated networks
                o Business-critical assets and processes
    - Active defense
    - Honeypot

1.5 - Explain the importance of efficiency and process improvement
in security operations.
**• Standardize processes**
    - Identification of tasks suitable for automation
                o Repeatable/do not require human interaction
    - Team coordination to manage and facilitate automation
**• Streamline operations**
    - Automation and orchestration
                o Security orchestration, automation, and response (SOAR)
    - Orchestrating threat intelligence data
                o Data enrichment
                o Threat feed combination
    - Minimize human engagement
**• Technology and tool integration**
    - Application programming interface (API)
    - Webhooks
    - Plugins
**• Single pane of glass**

2.0 Vulnerability Management

2.1 - Given a scenario, implement vulnerability scanning methods
and concepts.
**• Asset discovery**
    - Map scans
    - Device fingerprinting
**• Special considerations**
    - Scheduling
    - Operations
    - Performance
    - Sensitivity levels
    - Segmentation
    - Regulatory requirements
**• Internal vs. external scanning**
**• Agent vs. agentless**
**• Credentialed vs. non-credentialed**
**• Passive vs. active**
**• Static vs. dynamic**
    - Reverse engineering
    - Fuzzing
**• Critical infrastructure**
    - Operational technology (OT)
    - Industrial control systems (ICS)
    - Supervisory control and data acquisition (SCADA)
**• Security baseline scanning**
**• Industry frameworks**
    - Payment Card Industry Data Security Standard (PCI DSS)
    - Center for Internet Security (CIS) benchmarks
    - Open Web Application Security Project (OWASP)
    - International Organization for Standardization (ISO) 27000 series

2.2 - Given a scenario, analyze output from vulnerability assessment tools.
**• Tools**
    - Network scanning and mapping
                o Angry IP Scanner
                o Maltego
    - Web application scanners
                o Burp Suite
                o Zed Attack Proxy (ZAP)
                o Arachni
                o Nikto
    - Vulnerability scanners
                o Nessus
                o OpenVAS
    - Debuggers
                o Immunity debugger
                o GNU debugger (GDB)
    - Multipurpose
                o Nmap
                o Metasploit framework (MSF)
                o Recon-ng
    - Cloud infrastructure assessment tools
                o Scout Suite
                o Prowler
                o Pacu

2.3 - Given a scenario, analyze data to prioritize vulnerabilities.
**• Common Vulnerability Scoring System (CVSS) interpretation**
    - Attack vectors
    - Attack complexity
    - Privileges required
    - User interaction
    - Scope
    - Impact
                o Confidentiality
                o Integrity
                o Availability
**• Validation**
    - True/false positives
    - True/false negatives
**• Context awareness**
    - Internal
    - External
    - Isolated
**• Exploitability/weaponization**
**• Asset value**
**• Zero-day**

2.4 - Given a scenario, recommend controls to mitigate attacks and
software vulnerabilities.

**• Cross-site scripting**
\- Reflected
\- Persistent
**• Overflow vulnerabilities**
\- Buffer
\- Integer
\- Heap
\- Stack
**• Data poisoning**
**• Broken access control**
**• Cryptographic failures**
**• Injection flaws**
**• Cross-site request forgery**
**• Directory traversal**
**• Insecure design**
**• Security misconfiguration**
**• End-of-life or outdated components**
**• Identification and authentication failures**
**• Server-side request forgery**
**• Remote code execution**
**• Privilege escalation**
**• Local file inclusion (LFI)/remote file inclusion (RFI)**

2.5 - Explain concepts related to vulnerability response, handling,
and management.
**• Compensating control**
**• Control types**
    - Managerial
    - Operational
    - Technical
    - Preventative
    - Detective
    - Responsive
    - Corrective
**• Patching and configuration management**
    - Testing
    - Implementation
    - Rollback
    - Validation
**• Maintenance windows**
**• Exceptions**
**• Risk management principles**
    - Accept
    - Transfer
    - Avoid
    - Mitigate
**• Policies, governance, and service-level objectives (SLOs)**
**• Prioritization and escalation**
**• Attack surface management**
    - Edge discovery
    - Passive discovery
    - Security controls testing
    - Penetration testing and adversary emulation
    - Bug bounty
    - Attack surface reduction
**• Secure coding best practices**
    - Input validation
    - Output encoding
    - Session management
    - Authentication
    - Data protection
    - Parameterized queries
**• Secure software development life cycle (SDLC)**
**• Threat modeling**

3.0 Incident Response and Management
3.1 - Explain concepts related to attack methodology frameworks.
**• Cyber kill chain**
    - Reconnaissance
    - Weaponization
    - Delivery
    - Exploitation
    - Installation
    - Command and Control (C2)
    - Actions and objectives
**• Diamond Model of Intrusion Analysis**
    - Adversary
    - Victim
    - Infrastructure
    - Capability
**• MITRE ATT&CK**
**• Open Source Security Testing Methodology Manual (OSS TMM)**
**• OWASP Testing Guide**

3.2 - Given a scenario, perform incident response activities .
**• Detection and analysis**
    - IoC
    - Evidence acquisitions
                o Chain of custody
                o Validating data integrity
                o Preservation
                o Legal hold
    - Data and log analysis
**• Containment, eradication, and recovery**
    - Scope
    - Impact
    - Isolation
    - Remediation
    - Re-imaging
    - Compensating controls

3.3 - Explain the preparation and post-incident activity phases of
the incident management life cycle.
**• Preparation**
    - Incident response plan
    - Tools
    - Playbooks
    - Tabletop
    - Training
    - Business continuity (BC)/disaster recovery (DR)
**• Post-incident activity**
    - Forensic analysis
    - Root cause analysis
    - Lessons learned

4.0 Reporting and Communication

4.1 - Explain the importance of vulnerability management reporting
and communication.
**• Vulnerability management reporting**
    - Vulnerabilities
    - Affected hosts
    - Risk score
    - Mitigation
    - Recurrence
    - Prioritization
**• Compliance reports**
**• Action plans**
    - Configuration management
    - Patching
    - Compensating controls
    - Awareness, education, and training
    - Changing business requirements
**• Inhibitors to remediation**
    - Memorandum of understanding (MOU)
    - Service-level agreement (SLA)
    - Organizational governance
    - Business process interruption
    - Degrading functionality
    - Legacy systems
    - Proprietary systems
**• Metrics and key performance indicators (KPIs)**
    - Trends
    - Top 10
    - Critical vulnerabilities and zero-days
    - SLOs
**• Stakeholder identification and communication**

4.2 - Explain the importance of incident response reporting and
communication.
**• Stakeholder identification and communication**
**• Incident declaration and escalation**
**• Incident response reporting**
    - Executive summary
    - Who, what, when, where, and why
    - Recommendations
    - Timeline
    - Impact
    - Scope
    - Evidence
**• Communications**
    - Legal
    - Public relations
                o Customer communication
                o Media
    - Regulatory reporting
    - Law enforcement
**• Root cause analysis**
**• Lessons learned**
**• Metrics and KPIs**
    - Mean time to detect
    - Mean time to respond
    - Mean time to remediate
    - Alert volume
