---
source: https://xiph.org/video/vid1.shtml
---
# A Digital Media Primer for Geeks

<https://xiph.org/video/vid1.shtml>

Sound waves move through the air and are perceived by the human ear.  think of ripples in the water. Ears or microphones transfer these ripples of pressure into an electrical signal.  This signal is a one-dimensional value (a function , with a single value that varies over time).  At any given time, that value has real value and there is a smoothly variation of values throughout time; there is at  no time a point where the signal ceases to exist.

Digital signals are discrete in both value and time
![[./_resources/Untitled_Note.1.resources/unknown_filename.png]]

In the above, there are going to be points a fixed distance apart. 

![[./_resources/Untitled_Note.1.resources/unknown_filename.1.png]]

These discrete points provide us with a stream of digits to analyze.  

Now, while there is a similarity between a smooth analogue wave and the stepped, discrete digital number collection, we needed the work of C.E. Shannon and others to actually convert one to the other.  Their work produced what's called the **sampling theorem** which states not only can we go back and forth between analogue and digital signal, but creates the conditions where the conversion is **lossless.**  

Digital technology is technically older than analogue, given the invention of the telegraph.  Through the development of telegraph technology, the **Nyquist** frequency was discovered.  this frequency became the core of sampling sampling theorem.

**Digital Audio**

   with analogue, every new component brings with it a new potential source of distortion or noise. . Digital systems don't have such drawbacks, as digital signals can be manipulated, stored, or sent without adding any additional noise or distortion. (The exception is where the digital side of things meets the analogue, such as digitization or restoration.)

**Pulse Code Modulation**

Pulse code modulation is the most common representation for raw audio

![[./_resources/Untitled_Note.1.resources/unknown_filename.2.png]]

**raw PCM: sampling rate**
the highest frequency an encoding can represent is the **Nyquist frequency**.  In this context, the **Nyquist frequency is exactly half the sampling rate**.  the minimum sampling rate used today - in telephony for example - is 8kHz.
