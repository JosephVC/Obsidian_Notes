
• What are the advantages of using Solid State Drives over Hard Disk Drives, and how does  
wear leveling help extend the lifespan of a Solid State Drive?  
• What is Redundant Array of Independent Disks (RAID), and how does RAID 5 differ from  
RAID 1 in terms of fault tolerance and performance?  
• What are the benefits and drawbacks of using RAID 0 and RAID 1, and in what scenarios  
would each be appropriate?  
• How does RAID 10 combine the features of RAID 0 and RAID 1, and why is it suitable for  
high-performance applications?  
• What are the different types of secure digital (SD) cards, and how do their capacity and  
speed ratings differ?


- RAID
	- when building a RAID array, the smallest disk will determine the storage capacity of the whole array. build the array with consistent hardware
	- RAID 0 (Striping without parity) - striping splits the data into blocks and distributes it across all the disks; this allows multiple disks to serve requests in parallel. RAID 0 requires at least 2 disks and stripes the data. the logical volume size is the sum of the capacities of all the drives, which in practice means the size of the smallest drive limits the overall size
		- RAID 0 has no redundancy so if one disk fails the whole logical volume fails and necessitates backups
		- ![[Pasted image 20251005182524.png]]
	- RAID 1 (mirroring) - mirrored drive connection requiring two disks. each write operation is duplicated on the 2nd disk, thus there is a small performance overhead. read operations can use either disk, which boosts performance
		- simplest way to protect against single disk failure
		- when one disk fails and is replaced ASAP, the  new disk is populated with data from the other disk; RAID 1 rebuilds data faster than parity based RAID levels
		- ![[Pasted image 20251005183129.png]]
	- RAID 5 (Striping with Distributed Parity) - combines striping with distributed parity - needs a minimum of three disks
		- distributed parity means error correction is spread across all the disks, where the data and parity information are always on different disks
		- if a single disk fails, the information can be reconstructed from data on the other disks
		- excellent read performance, but if a disk fails read performance slows down because the system needs to use parity information to rebuild data
		- as you add more storage space the fault tolerance decreased 
		- one third of each disk in RAID 5 is used for parity, so with three 80Gb disks, you end up with 160Gb of usable space
		- ![[Pasted image 20251005184835.png]]
	- RAID 6 (striping with double parity) - uses striping with dual distributed parity, so spreads two sets of parity information across all disks
		- allows failure of two disks
		- greater fault tolerance than RAID 5
		- ![[Pasted image 20251006045251.png]]
		- 
	- RAID 10 (strip of mirrors) - uses a striped volume with mirrored arrays
		- high fault tolerance, as  one disk can fail without overall data loss
		- ![[Pasted image 20251005185402.png]]


SD cards also have different speed ratings:  
• Original SD: Up to 25 MBps.  
• UHS (Ultra High Speed): Up to 108 MBps.  
• UHS-II: Up to 156 MBps full-duplex or 312 MBps half-duplex.  
• UHS-III: Up to 312 MBps (FD312) or 624 MBps (FD624) full-duplex.  
• SD Express: The latest variant, which combines the SD card form factor with PCIe and NVMe  
interfaces, offers speeds up to 985 MBps.

Each optical disc type has different capacities and transfer rates:  
	• CD:  
		• Capacity: Up to 700 MB.  
		• Formats: Recordable (CD-R) and Rewritable (CD-RW).  
		• Base Transfer Rate: 150 KBps.  
	• DVD:  
		•   Capacity: 4.7 GB (single-layer, single-sided) to about 17 GB (dual-layer, double-sided).  
		• Formats: DVD+R/RW and DVD-R/RW (most drives support both, indicated by the ±  
		symbol).  
• Base Transfer Rate: 1.32 MBps (equivalent to 9x CD speed).  
• Blu-ray:  
• Capacity: 25 GB per layer.  
• Base Transfer Rate: 4.5 MBps, with a maximum theoretical rate of 16x (72 MBps).