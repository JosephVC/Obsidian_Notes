---
---
**Tagged Template Literals**

Using backticks, you can substitute values returned by functions

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals.jpg]]

even though this doesn't seem to be doing anything, the power of the template literal is that it is split into pieces by the JVM, then passed to the tag as arguments; this allows a more refined control over the template literal 

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - split tags.jpg]]

for some reason there will always be one extra string literal than what is defined

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - extra stri.jpg]]

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - extra stri.1.jpg]]

There is a way to reconstruct the template literal to give a more sensible value:

Apparently to get any sort of sensible output, you need a more involved function to allocate values to the template literal

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - sensible o.jpg]]

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - reconstruc.PNG]]

Here is an example of using another function to parse the template literal.  

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - using func.PNG]]

The reason the strings and interpolated values are handled separately are because it would be too confusing to try and handle them all at the same time. 

You should also use semicolons when using tagged template literals. 

![[./_resources/Untitled_Note.7.resources/javascript - tagged template literals - use semico.PNG]]
