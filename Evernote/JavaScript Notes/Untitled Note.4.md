---
---
**New Number Methods**

Infinity is not the same as negative Infinity

![[./_resources/Untitled_Note.4.resources/unknown_filename.1.png]]

the **.isFinite()** methods clearly checks whether a given **number** is finite or not; it will return **false** when given a string

![[./_resources/Untitled_Note.4.resources/unknown_filename.png]]

**all numbers in JS are floating point**

![[./_resources/Untitled_Note.4.resources/unknown_filename.2.png]]

**WAIT A DAMN MINUTE**

![[./_resources/Untitled_Note.4.resources/unknown_filename.3.png]]

Regardless of the above, when numbers move beyond the above ranges, the floating point arithmetic becomes imprecise (**why**)

example: 

![[./_resources/Untitled_Note.4.resources/unknown_filename.4.png]]

the method **.isSafeInteger()** checks if we are within the safe bounds

![[./_resources/Untitled_Note.4.resources/unknown_filename.5.png]]

a final math method is **Math.pow()**, which takes two arguments; its first argument is raised to the power of the second argument

**Math.pow(2, 3) == 8**
