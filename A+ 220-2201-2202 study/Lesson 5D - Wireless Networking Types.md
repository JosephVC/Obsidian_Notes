
• What type of mode are most wireless networks configured in?  
• What are the three main frequency bands used by wireless networks?  
• You notice that your wireless network has been running slow lately. You perform a wireless  
analysis of the area and notice there are multiple wireless networks running on the same  
frequency. What would be the best solution to try to speed up your wireless network?  
• What technology increases reliability and bandwidth by multiplexing signal streams from  
multiple antennas?  
• Which wireless technology is primarily used for contactless payment?


- **Access Points** 
	- use radio waves as a transmission medium
	- most wifi networks are initially configured in 'infrastructure mode'
		- each client device is set to connect to the overall network via an access point
			- this is referred in the 802.11 documentation as a **Basic Service Set (BSS)**
		- the MAC address of the access point's radio is the **basic service set ID (BSSID)**
	- a wireless network can establish wireless-only network and also work as a bridge between wireless networks and wired networks
		- the wired network is the **distribution system (DS)**
		- the access point will be connected somewhere like a client computer - via an ethernet cable and wall port
		- many access points will be power via PoE
	- Installation
		- the network name of a wireless access point is the **service set identifier (SSID)**
		- channel bonding is usually most feasible in the 5Ghz range
		- configure security parameters

- **Frequency Bands**
	- license frequency
		- someone has purchased exclusive rights to use a particular band of frequency via the FCC
			- if this given band of frequency is interrupted the owner has the right to sue
	- public frequency
		- unlicensed
		- 900Mhz, 2.4Ghz, 5Ghz
		- because anyone can use these frequencies, interference is a risk
		- power output of public frequencies is regulated
			- **transmit power** is measured in dBm and is the basic strength of the radio
			- **gain** is the amount of signal boosted by directionality
				- focus the signal rather than have it spread
				- measured in decibels per isotropic
			- Effective isotropic radiated power EIRP 
				- sum of the transmit power and gain, dBm
	- modulation - technique used to modify a radio wave so it can carry data
	- frequency bands are split into different sub ranges of frequency called **channels**
	- 2.4Ghz - better at going through solid surfaces and has the longest signal range
		- cannot support a high number of channels and thus can get congested with other wifi bands and other wireless tech such a bluetooth - even microwave ovens
			- supports up to 14 channels
		- higher risk of interference
			- channels 1, 6, 11 do not overlap
			- USA restricts  use to channels 1-11
				- other countries allow more channels to be used
		- lower max data rates
		- range of 45m
	- 5Ghz - less effective at going through solid surfaces
		- less max. range than 2.4Ghz
			- 30m
		- supports more individual channels so suffers from less interference
		- 
	- 6Ghz - suck even more than 5Ghz at penetrating solids
		- very fast and can support more channels than 2.4 or 5Ghz
		- range of 15m
	- 802.11a
		- uses 5g only
	- 802.11b/g
		- uses 2.4Ghz
		- encoding sucks compared to 802/a and only supports 11Mbps
		- uses **Direct-Sequence Spread Spectrum(DSSS)** modulation 
			- spreads signal across a wider channel (22Mhz) to improve resistance to interference
	- 802.11g
		- 2.4 Ghz 
		- 54Mbps
		- uses **Orthogonal Frequency division Multiplexing (OFDM)** 
			- uses 20Mhz
			- more efficient and allows more data to be sent across a smaller channel
	- 802.11n
		- works  over 2.4Ghz and 5Ghz
		- allows two adjacent 20Mhz channels to be combined into a 40Mhz - channel bonding
		- uses MIMO - multiple input multiple output
		- 72Mbps or 150 for dual channels
		- wifi 4
	- 802.11ac
		- wifi 5
		- 5Ghz
		- can also  use 2.4
		- tri band
		- 433Mbps
		- allows for 80 and 160Mhz bonded channels
		- access points are marked by AC values, such as AC5300
			• 1,000 Mbps over a 40 MHz channel with 2x2 streams on the 2.4 GHz radio.  
			• 2,166 Mbps over an 80 MHz bonded channel with 4x4 streams on the first 5 GHz radio.  
			• 2,166 Mbps on the second 5 GHz radio.

	- 802.11ax
		- wifi 6
		- marked by AX values
		- rates up to 1148 Mbps on 2.4Ghz or 4804 Mbps on 5Ghz
		- supports up to 8 clients
		
	- 802.11be
		- wifi 7
		- 2.4 Ghz, 5Ghz, 6Ghz
		- uses channels up to 320Mhz on 6Ghz for speeds up to 46Gbps
		- ability to use Multi-Resource Unit (MRUs)
			- each channel at 6Ghz is broken down into smaller channels called MRUs
				- these smaller channels can each be different sizes


		  
		