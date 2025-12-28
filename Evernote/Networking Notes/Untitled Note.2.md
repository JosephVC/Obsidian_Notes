---
---
**Asynchrony**

the time it takes for a server and browser to process requests is non-standard, as the time involved in such tasks depends on payload size, latency, and other processing times).  Asynchrony is used to handle such variation.  compare this with **synchronous**  programming, where operations are performed in the order they occur.  in asynchronous programming, statements may be read in a linear order but are not processed in that same order:

![[./_resources/Untitled_Note.2.resources/unknown_filename.2.png]]

In network programming, operations often take variables amounts of time to complete 

Initially, this was dealt with using callbacks, which while fast and efficient, could be difficult to read and debug:
![[./_resources/Untitled_Note.2.resources/unknown_filename.1.png]]

later, the concept of a **promise** was developed.  Rather than call a nested variety of functions, create a reusable object that could call the next function in a series once the previous function completed:
![[./_resources/Untitled_Note.2.resources/unknown_filename.png]]
![[./_resources/Untitled_Note.2.resources/unknown_filename.3.png]]

The difference between the two sections of code regard readability and organization; in the latter example the code follows an if/then structure where all the necessary functions are spelled out rather than being drawn in from somewhere else in the code

The above can be made much simpler by using an **async function**, which compresses much of the above code  to improve legibility:
![[./_resources/Untitled_Note.2.resources/unknown_filename.4.png]]

In the above, normal functions are turned into a promise; this allows us to use more condensed code that still functions asynchronously
