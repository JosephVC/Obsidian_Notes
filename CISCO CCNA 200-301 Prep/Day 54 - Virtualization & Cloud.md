---
---
**Server Hardware**

* Cisco also offers hardware servers, such as UCS (Unified Computing System)
* the largest vendors of hardware servers include Dell EMC, HPE, and IBM

**Servers before Virtualization**
![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.png]]

* before virtualization, there was a one-to-one relationship between a physical server and an operating sytem
* in the operating system, web servers and email servers would run as applications
	* one physical server would be used for the web, another for email, a database server, etc.
	* this is inefficient for several reasons
		* each physical server is expensive and takes up space, power, etc.
		* the resources on each physical server (CPU, RAM, storage, NIC) are typically under-used

**Virtualization (Type 1 Hypervisor)**

* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.1.png]]
* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.8.png]]
	
* virtualization allows us to break the one-to-one relationship of hardware to OS, allowing multiple OSs to run on a single physical server
* each instance is called a Virtual Machine
* a **hypervisor** is used to manage and allocate the hardware resources (CPU, RAM, etc.) to each VM
	* another name for a hypervisor is **VMM (Virtual Machine Monitor)**
* the type of hypervisor which runs directly on top of the hardware is called a **Type 1** hypervisor
	* examples includes VMware ESXi, Microsoft Hyper-V, etc.
	* type 1 hypervisors are also called **bare-metal hypervisors** because they run directly on the hardware
		* another name for these is **native hypervisor**
		* this is the type of hypervisor used in data center environments

**Type 2 Hypervisor**

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.2.png]]

	
* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.9.png]]
	these run as regular programs on another operating system
	
	
* the OS running directly on the hardware is called the **Host OS,** and the OS running in a VM is called a **Guest OS**
* another name for a Type 2 hypervisor is a **hosted hypervisor**
* Although Type 2 hypervisors are rarely used in data center environments, they are common on personal--use devices

**Why Virtualization**

* **partitioning-** run multiple operating systems on one physical machine
	* divide system resources between virtual machines
* **isolation -** provide fault and security isolation at the hardware level
	* preserve performance with advanced resource controls
* **encapsulation -** save the entire state of a virtual machine to files
	* move and copy virtual machines as easily as moving and copying files
* **hardware independence** - provision or migrate any virtual machine to any physical server
* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.3.png]]

**Connecting VMs to the Network**
![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.4.png]]

* VMs are connected to each other and the external network via a virtual switch running on the hypervisor
* as with a regular switch, the vSwitch's interfaces can operate as access or trunk ports and use VLANs to separate the VMs at Layer 2
* interfaces on the vSwitch connect to the physical NIC(s) of the server to communicate with the external network

**Cloud Services**

* traditional IT infrastructure deployments were some combination of the following
	* **on-premises**
		* all servers, network devices, and other infrastructure are located on company property
		* all equipment is purchased and owned by the company using it
		* the company is responsible for the necessary space, power, and cooling
	* **colocation**
		* data centers that rent out space for customers to put their infrastructure (servers, network devices)
		* the data center provides the space, electricity, and cooling
		* the servers, network devices, etc, are still the responsibility of the end customer, although they are not located on the customer's premises
	* cloud services provide an alternative that is hugely popular and is continuing to grow
	* most people associate cloud with public providers such as AWS
* NIST (National Institute of Standards and Technology) defines cloud computing in SP (Special Publication) 800-145:
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.5.png]]
* **the CCNA expects you to understand the following:**
	* 5 essential characteristics
	* 3 service models
	* 4 deployment models

**5 Essential Characteristics of Cloud**

* **On-demand self-service** 
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.7.png]]
	* the customer is able to use the service freely without direct communication with the service provider
* **Broad network access**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.6.png]]
	* the service is available through standard network connections (Internet or private WAN connections) and can be accessed through many kinds of devices
* **Resource pooling**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.8.png]]
	* a pool of resources is provided by the service provider, and when a customer requests a service (such as creating a new VM), the resources to fulfill that request are allocated from the shared pool
* **Rapid elasticity**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.9.png]]
	* customers can quickly expand the services they use in the cloud - expanding storage or adding VMs - from a pool that look infinite.  likewise, they can quickly reduce their services when not needed
* **Measured Service** 
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.10.png]]
	* the cloud service provider measures the use of cloud resources, and the customer can measure their own use as well; customers are charged based on usage

**3 Service Models of Cloud**

* in cloud computing, everything is provided on a service model
* rather than end users buying and setting up a physical server
* There is a variety of **\_\_\_ as a service** models out there
	* **Software as a Service (SaaS)**
		* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.13.png]]
		* Microsoft Office 365 is an example of this
			* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.12.png]]
	* **Platform as a Service (PaaS)**
		* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.11.png]]
		* Examples includes AWS Lambda and Google App Engine
	* **Infrastructure as a Service (IaaS)**
		* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.14.png]]
		* Examples include Amazon EC2 or Google Compute Engine
			* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.15.png]]

**The Four Deployment Models of Cloud**

* the public cloud - AWS, Azure, GC, etc. are not the only cloud models
* **Private Cloud**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.16.png]]
	* private clouds are generally used by large enterprises
	* while the cloud is private, it is owned by a third party
		* AWS provides services to the DoD
	* private clouds may be on or off premises
		* 'cloud' and 'on premises' are not always two different things
	* the same kinds of services offered are the same as in public clouds (PaaS, SaaS, IaaS) but the infrastructure is reserved for a single organization
* **Community Cloud**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.17.png]]
	* this is the least common cloud deployment
	* similar to private cloud, but the infrastructure is reserved for use by only a specific group of organizations
* **Public Cloud**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.18.png]]
	* by far the most common cloud deployment
	* the most popular cloud providers
		* AWS
		* Azure
		* GCP
		* OCI (Oracle Cloud Infrastructure)
		* IBM Cloud
		* Alibaba Cloud
* **Hybrid Cloud**
	* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/unknown_filename.19.png]]
	* basically any combination of the previous three deployment types
	* example, a private cloud which can offload to a public cloud when necessary

**Benefits of Cloud Computing**

* **Cost**
	* CapEx(Capital Expenses) of buying hardware and software, setting up data centers, etc. are reduced or eliminated
* **Global Scale**
	* cloud services can scale at a rapid pace; services can be set up and offered to customers from a geographic location close to them
* **Speed/Agility**
	* services are provided on demand, and vast amounts of resources can be provisioned within minutes
* **Productivity**
	* cloud services remove the need the time-consuming tasks of buying servers and setting them up
* **Reliability**
	* backups in the cloud are very easy to perform; data can be mirrored in multiple sites in different geographic locations to support disaster recovery

**Connecting to Cloud Resources**

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.png]]
**Data and Control Plane**

	A network device contains the following planes:
	
* **Control plane -** This is typically regarded as the brains of a device. It is used to make forwarding decisions. The control plane contains Layer 2 and Layer 3 route forwarding mechanisms, such as the IPv4 and IPv6 routing tables, and the ARP table. Information sent to the control plane is processed by the CPU.
* **Data plane -** Also called the forwarding plane, this plane is typically the switch fabric connecting the various network ports on a device. The data plane of each device is used to forward traffic flows. Routers and switches use information from the control plane to forward incoming traffic out the appropriate egress (outgoing) interface. Information in the data plane is typically processed by a special data plane processor without the CPU getting involved.
* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.10.png]]
	

**QUIZ**

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.1.png]]

* A

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.2.png]]

* A

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.3.png]]

* D

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.4.png]]

* C

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.5.png]]

* D

![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.6.png]]

* B
* ![[./_resources/Day_54_-_Virtualization_&_Cloud.resources/image.7.png]]
