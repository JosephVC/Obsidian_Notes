---
---
![[./_resources/Encapsulation.resources/unknown_filename.png]]

As data goes through different layers, data about each respective layer is added.  At the Network layer, the Layer 3 header would contain the destination IP address, whereas the Transmission layer would add data about the protocol being used.  the Data Link layer adds a header and **trailer** to ensure the data has not been corrupted; this also helps prevent tampering or corruption of the data.  this whole process is called **encapsulation.**  Each layer adds to the encapsulation differently, and the data is given different names at certain layers, such as where data is referred to as a **packet** at the Network layer.  

This whole process is reversed when the data is received.  this is **de-encapsulation**.  All computers with networking capabilities do this sort of encapsulation and de-encapsulation.  this allows standardized ways of sending data between computers, where all transmissions follow the same methodology and any network-capable device can send a request to any other and have it understood.
