---
---
**Arrow Functions**

there are a whole lot of different ways to define functions 

![[./_resources/Untitled_Note.5.resources/unknown_filename.png]]

there is a way to create a function to return callbacks, but it looks awkward

![[./_resources/Untitled_Note.5.resources/unknown_filename.1.png]]

the arrow function look a lot cleaner and is easier to read:  **take an array of values and map them to return the given value (x) \*2**

the above function did not need parens, but if you pass zero or more than one argument to an arrow function, then you need to close it within parentheses

![[./_resources/Untitled_Note.5.resources/unknown_filename.2.png]]

Apparently, when you ask for a given value returned with with an arrow function and with no other arguments, that number gets mapped to whatever values you have in the array

in the below example, we map the given item in the array together with its index, and return that item's index

![[./_resources/Untitled_Note.5.resources/unknown_filename.3.png]]

You can use rest parameters and destructuring with arrow functions as well

![[./_resources/Untitled_Note.5.resources/unknown_filename.4.png]]

Yout can fit a simple arrow function on a single line:

![[./_resources/Untitled_Note.5.resources/unknown_filename.5.png]]

Below is the same as above:

![[./_resources/Untitled_Note.5.resources/unknown_filename.6.png]]

Note that if you do a multi-line function you will need a **return** statement

![[./_resources/Untitled_Note.5.resources/unknown_filename.7.png]]

it is possible to get confused when multiline functions are being created and when objects are being created; when  you are creating a function, you need to wrap the curly brackets in parens

![[./_resources/Untitled_Note.5.resources/unknown_filename.8.png]]

arrow functions can make **bind** statements easier to use; like in other multiline statments, you will need the **return** statement

![[./_resources/Untitled_Note.5.resources/unknown_filename.9.png]]

a power of the arrow function is that is sees everything in its scope, so **this** works

Keep in mind you don't need the backticks and dollar signs if you are return non-string values

![[./_resources/Untitled_Note.5.resources/unknown_filename.10.png]]

again, **arrow functions always inherit the scope they are defined in**
