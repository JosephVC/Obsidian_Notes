
• What are the four basic operations performed by the CPU on each instruction, and how can  
understanding these operations help in optimizing server performance?  
• What are the key differences between ARM's RISC architecture and the CISC architecture  
used in x86/x64 CPUs, and how do these differences impact performance and power  
efficiency?  
• What is Simultaneous Multithreading (SMT), and how does it enhance performance in  
multithreaded applications?  
• What is the difference between Intel's Land Grid Array (LGA) and AMD's Pin Grid Array  
(PGA) socket types, and why is it important to match the CPU and motherboard socket  
types?  
• What are the differences between Intel's Core i3/i5/i7/i9 processors and AMD's Ryzen  
3/5/7/9 processors, and how do these differences impact the choice of desktop computers  
for office use?  
• What are the key features of server-class CPUs like Intel Xeon and AMD EPYC, and why are  
these features important for data center operations?


Basic CPU instructions:
1. fetch - the control unit fetches the next instruction in the sequence from memory into the pipeline
2. decode - the control unit decodes each instruction and will either execute it or pass it to the arithmetic logic unit (ALU) or the floating point unit (FPU) for execution
3. execute - either the ALU or the FPU executes the instruction
4. write-back - the result of the executed instruction is written back to a register, cache, or system memory
	1. a register is a temporary storage area within the CPU operating at the same clock speed as the CPU
	2. a cache is a small portion of memory working at or near the speed of the CPU (depending on the cache level). frequently used instructions and data are stored in the cache. cache is used to reduce the time needed to access this information. these optimize performance as the CPU does not have to rely on slower system memory
		1. L1 cache is the fastest and smallest and integrated directly into the CPU core

Main types of CPU architecture
1. RISC - example are the PowerPC CPUs that Apple used - better for mobile and embedded devices as it uses a smaller, optimized set of instructions. thus executes faster and with less power. 
2. CISC - example is the x86 architecture - uses a larger instruction set and allows for  more complex operations. this in turn simplifies programming and allows general-purpose tasks to be more performative. suitable for desktops and servers

x64 CPU architecture
- supports Data Execution Prevention - preventing code code execution from non-executable memory regions

ARM CPU architecture
- ARM = Advanced RISC machines
- made by qualcomm, Nvidia, Apple, Samsung, etc.
	- Apple M1 and M2 chips
- uses system-on-a-chip to integrate other components like video, sound, networking, and storage controllers on to the CPU, allowing ARM to be very compact
- traditionally soldered directly to the motherboard

CPU features
- simultaneous multithreading - same as Intel Hyperthreading - allows multiple instruction streams (threads) from software to be processed concurrently - done at the same time. this reduces CPU idle time and enhances performance when applications support multithreading
	- multithreading allows each physical CPU core - the physical processor - to act like two cores
- symmetric multiprocessing - uses two or more physical cores and can distribute tasks across multiple CPUs, regardless of whether they are multithreaded. more common in servers and high-end workstations
- zero insertion force (ZIF) - allows CPUs to be installed without damaging the pins
- Intel Land Grid Array (LGA) - pins are located on the motherboard socket and the CPU has the contact pads
	- LGA 1200 - 10th and 11th gen Intel core processors and compatible with Comet Lake and Rocket Lake CPUs
	- LGA 1700 - for the 12gen Alder lake
- AMD Pin Grid Array (PGA) sockets - pins are located on the CPU itself and fit into the motherboard socket
	- AM4 - used in Ryzen processor
	- TR4 - for the Threadripper 
	- SP3 - for EPYC server processors and use the LGA socket for better durability and performance