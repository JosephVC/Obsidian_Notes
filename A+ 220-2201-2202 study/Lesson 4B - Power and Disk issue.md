
• What steps would you take to diagnose a computer that won't start due to a power issue?  
• What should you do if the computer powers on but does not start, showing a black screen  
with no beeps?  
• What should you check if a fixed disk is not detected during boot?  
• What are the two ways of formatting boot information, and how do they differ?  
• What should you do if a Windows system displays a blue screen of death (BSOD)?  
• What are common symptoms of a failing hard disk drive (HDD)?


To isolate the cause of no power, try the following tests:  
1. Check other equipment: Ensure other devices in the area are working to rule out a power  
circuit fault or a blackout.
2. Test the wall socket: Plug a known-good device, like a lamp, into the wall socket. If it doesn't  
work, the socket is faulty. Contact an electrician.  
3. Verify PSU connections: Ensure the PSU is properly connected to the PC and wall socket,  
and all switches are in the "on" position.  
4. Try another power cable: There may be an issue with the plug or fuse. Check the plug's  
wiring and fuse resistance with a multimeter or swap with a known good fuse.  
5. Disconnect extra devices: Remove devices like a plug-in graphics card. If this solves the  
problem, the PSU may be underpowered, or one of the devices is faulty.  
6. Test the PSU: If safe, use a multimeter or power supply tester to check the PSU.  
Technician working with a power supply tester

*PC power supplies are not meant to be serviced by users. never remove the cover or try to fuck with them yourself without training*

POST = Power On Self Test
- diagnostic program that implements the system's firmware that checks the hardware components needed to boot the computer

If power is present (e.g., you hear the fans spinning) but the computer does not start, shows a  
blank screen, and there are no beeps from the internal speaker, it is likely either a display issue  
or the POST procedure is not executing. Assuming the display is not the issue, try the following:  
1. Ask what has changed—If the system firmware has been updated and the PC has not  
booted since then, the system firmware update may have failed.  
Use the reset procedure.  
2. Check cabling and connections—Especially if maintenance work has just been performed,  
ensure all cables and adapter cards are correctly seated. An incorrectly oriented storage  
adapter cable or a poorly seated adapter card can stop POST from running.  
Correct any errors, reset adapter cards, and then reboot the PC.  
3. Check for faulty interfaces and devices—A faulty adapter card or device may halt POST.  
Remove one device at a time to identify the faulty component, or remove all non-essential  
devices and add them back one by one.  
4. Check the PSU—Even if the fans are receiving power, there may be a fault preventing the  
power good signal from being sent to the CPU, stopping POST.  
5. Check for a faulty CPU or system firmware—If possible, replace the CPU chip with a known  
good one or update the system firmware


certain computers have little switches called jumpers used to configure boot modes or processor settings; incorrect jumper settings can prevent the computer from booting correctly; make sure the jumpers weren't changed if things don't boot properly


![[Pasted image 20251102153549.png]]

some computers won't boot if a key is stuck; make sure nothing is resting on the keyboard

Boot disk formatting
- MBR
	- Master Boot Record
		- located in the first sector of the partitioned disk
		- holds information  about disk partitions and contains code regarding location of the active boot sector
		- boot sector is located after the MBR or the first partition of the HDD
		- contains the Boot Configuration Record (BCR) for Windows or other boot managers like GRUB or LILO in Linux
		- only one primary partition can be marked as active for booting
- GPT
	- GUID Partition Table
	- identifies partitions and OS boot loaders
	- not limited to a single sector


signs of drive failure
- odd noise like clicking or grinding
- no LED activity if activity lights are plugged in; for a RAID array this can indicate one drive failed
- constant activity indicates disk thrashing; could be caused by constant paging to the disk if there is not enough RAM, faulty software, malware, or a failing disk
- bootable device  not found - possible file corruption or faulty drive; RAID controller fails to detect one or more drives in an array so one goes 'missing'
- missing drives in OS - if a file explorer or command line cannot detect a drive, there is likely hardware/connector faults
- Read/Write failures - 'cannot read from source disk' signs of a bad sector in HDD or bad blocks in an SSD; run a diagnostic check like chkdsk to identify bad sectors
- Audible alarms - high end drives or RAID controllers have actual audible alarms if shit blows up
- BSOD - severe drive issues can cause a BSOD or similar error in the OS
- SMART
	- Self Monitoring Analysis and Reporting Technology
		- can alert the system if a failure is detected 
		- run this diagnostic if you think there are a drive is failing or experiencing performance issues
- IOPS 
	- Input/Output operations per second 
	- performance  metrics that can indicate hardware issues

file recovery on an SSD is usually not possible without specialized tools


Troubleshoot RAID failure
- RAIDs are meant to be redundant and protect against data loss by mirroring or backing up data to other drives
- RAID 0 has no redundancy, where if a disk fails the volume stops working; this is used where speed is the top priority
- there are hardware and software controllers for RAID arrays
- Main scenarios where RAIDs fail
	- device failure
		- volume will be listed as degraded but data could still be accessible  can might be bootable
		- array failure
			- desktop-tier RAIDs can tolerate one disk failing
			- the controller can then rebuild the array 
	- if you remove a healthy disk that can also cause an array failure; often a red LED is flashing when a drive fails
	- always back up data before swapping drives
- Unavailable volume or 'array missing' - if a volume is not available, either more disks have failed than the array can handle or the controller has failed
	- if the boot volume is affected, the OS will not start
	- backup and recover if too many disks have failed
- 
