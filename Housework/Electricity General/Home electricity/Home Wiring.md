
- Amps, volts, watts
	- amps - measures electrical current, or the speed at which the electrons flow through a conductor 
		- represented by the letter "I"
		- equivalent to the flow rate of water through a pipe
	- volts - the measure of electrical potential between any two points in an electrical circuit
		- equivalent to water pressure
		- represented by the letter "V"
		- V = I * R
	- ohms - the resistance in a conductor
		- represented by "R" in equations
		- equivalent to the diameter of a water hose
	- watts - the power output of a given device
		- watts = volts * amps
		- P=V * I
- measure in series
	- 
- Twisted Pair Wiring
	-  both outgoing noise and incoming noise are reduced
		- a magnetic field is generated when AC current is passed through a wire
		- when a magnetic field interacts with an electrical circuit, an electrical current will be generated within the circuit
		- based on the above, a signal within one circuit can jump to a nearby one via **induction**
			- the jumping of signals can also be called crosstalk
		- if you run a positive signal through one wire and a negative one through the other one, the positive and negative fields will work against and cancel each other via **destructive interference**
	- Common mode rejection
		- as the signals in the two wires are of opposite voltage, they should cancel each other out
		- the device receiving the signal can be configured to check whether the wires have the opposite voltage
		- if there is magnetic interference along the path of the wires, it will generate a voltage that is the same in each wire
		- in common mode rejection, the signal is rejected  if the device sees the wires as having the same voltage, as it was likely interfered with


https://audiouniversityonline.com/twisted-pairs/