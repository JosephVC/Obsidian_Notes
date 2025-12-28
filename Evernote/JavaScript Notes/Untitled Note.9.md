---
---
**Generators**

certain things are not iterable by **for...in** or **for...of**, so we create generators as a way of  making a different type of iterable object

![[./_resources/Untitled_Note.9.resources/javascript - basic generators.png]]

placing a star \* by the keyword **function\*** creates a generator, so now that when we call that function it now can be iterated over, with the keyword **yield** providing one value as we step through the now-iterable function

for every time **n** steps through **numbers**, we get the latter to **yield** a number

every time yield is run, the function will stop to return the value, the code in the for loop is run based on the yielded value
![[./_resources/Untitled_Note.9.resources/javascript - generators detail.png]]

Here are more examples of generators.  Note that the reason the output starts at 0 is because the variable i is initialized at 0

![[./_resources/Untitled_Note.9.resources/javascript - basic generators 2.png]]

![[./_resources/Untitled_Note.9.resources/javascript - basic generators example.png]]
