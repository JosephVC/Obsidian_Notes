---
---
**Configuration Drift**

* when individual changes made over time cause a device's configuration to deviate from the standard/correct configurations as defined by the company
	* although each device will have unique parts of its configuration (IP address, etc.) most of a device's configuration is usually defined in standard templates designed by the network architects/engineers of the company
	* as individual engineers make changes to devices - in order to troubleshoot/fix networking issues, test configurations - the configuration of a device can drift away from the standard
		* record these individual changes and the reason, because often they are not kept
* even with automation tools, it is best to have a standard **configuration management** practice
	* when a change is made, save the config as a text file and place it in a shared folder
		* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/image.png]]
		* it's possible an engineer will forget to place a new config in the folder after making changes, so there is confusion as to which is the correct file
		* even if configurations are properly saved like this, it doesn't guarantee that the configurations actually match the standard

**Configuration Provisioning**

* this refers to how configuration changes are applied to devices
	* this includes configuring new devices, too
* traditionally, configuration provisioning is done by connecting to devices one-by-one via SSH
	* this is not practical in large networks
* tools like Ansible, Puppet, and Che allow us to make changes to devices on a mass scale with a fraction of the time/effort
* these tools use two essential components: **templates** and **variables**
	* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/image.1.png]]

**Configuration Management Tool**

* these tools are network automation tools that facilitate the centralized control of large numbers of network devices
* the options you need to be aware of for the CCNA are Ansible, Puppet, and Chef
* these tools were originally created after the rise of VMs, to enable server system admins to automate the process of creating, configuring, and removing VMs
	* however, they are also widely used to manage network devices
* these tools can be used to perform tasks such as
	* generate configurations for new devices on a large scale
	* perform configuration changes on devices (all or a certain subset of devices)
	* check device configurations for compliance with defined standards
	* compare configurations between devices, and between different versions of configurations on the same device

**Ansible**

* configuration management tool owned by Red Hat
* written in Python
* is **agentless**
	* does not require any special software to run on the managed devices
* uses SSH to connect to devices, make configuration changes, extract information, etc.
* uses the **push model**
	* the Ansible server- the Control node - uses SSH to connect to managed devices and **push** configuration changes to them
	* Puppet and Chef us a **pull** model
* After installing Ansible, you must create several text files
	* **Playbooks** - these are files working as **blueprints of automation tasks** written in YAML; they outline the logic and actions of the tasks that Ansible should do
	* **Inventory -** these files list the devices that will be managed by Ansible, as well as characteristics of each device such as their device roles (access switch, core switch, router, firewall, etc.) written in INI, YAML, or other formats
	* **Templates -** these files represent a device's configuration file, but specific values for variables are not provided; written in Jinja2
	* **Variables -** these files list variables and their values; these values are substituted into templates to create complete configuration files; written in YAML
* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/image.2.png]]

**Puppet**

* config tool written in Ruby
* typically **agent-based**
	* specific software must be installed on the managed devices
	* not all Cisco devices support a Puppet agent
* **can be run agentless** in which a proxy agent runs on an external host, and the proxy agent uses SSH to connect to the managed devices and communicates with them
* the Puppet server is called the **Puppet Master**
* Puppet  uses a pull model - clients pull configurations from the Puppet master
	* Clients use TCP 8140 to communicate with the Puppet master
* instead of YAML, it uses a proprietary language for files
* text files are required on the Puppet master include
	* **Manifest:** this file defines the desired configuration state of a network device
	* **Templates:** similar to Ansible temples.  used to generate Manifests
* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.png]]

**Chef**

* like Puppet, is a configuration management tool written in Ruby
* Chef is agent-based
	* specific software must be installed on the management devices
	* not all cisco devices support a Chef agent
* Chef uses a **pull model**
* the server Chef uses is TCP 1002 to send configuration to clients
* files use the **DSL (Domain-Specific Language)** based on Ruby
* Text files used by Chef include:
	* **Resources:** the ingredients of a recipe; these are configuration objects managed by Chef
	* **Recipes:** the recipes of a cookbook; these outline the logic and actions of the tasks performed on the resources
	* **Cookbooks:** a set of related recipes grouped together
	* **Run-list:** an ordered list of recipes that are run to bring a device to the desired configuration state
* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.1.png]]

![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.2.png]]

**QUIZ**

1. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.4.png]]
	* B

2. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.3.png]]
	* A, C

3. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.5.png]]
	* D
		* all use a server/client in some form

4. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.7.png]]
	* A, C

5. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.9.png]]
	* B

6. ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.8.png]]
	* D
	* ![[./_resources/Day_63_-_Ansible,_Puppet,_Chef.resources/unknown_filename.6.png]]
