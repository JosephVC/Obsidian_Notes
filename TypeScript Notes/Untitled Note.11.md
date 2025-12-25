---
---
**Function Types**

a function type is something like **(n: number) => number** 

what the above translate to is "a function that takes a number and which returns a number"

the idea here is to be explicit as to what sort of types we allow a function to take as well as return

![[./_resources/Untitled_Note.11.resources/typescript - function types.jpg]]

here, we create a function that just returns nothing but a number

we then set a variable calling that function which then calls the five() function (which actually return something, in this case the number 5)

![[./_resources/Untitled_Note.11.resources/typescript - function types2.jpg]]

we're allowed to have a function take a number and return a string, so far as we make sure to convert the number to the string

That doesn't happen in the above, so then we  have our Takes... function call the add1 function (which adds and returns a  number) and try to return a string, which ultimately results in a type error

![[./_resources/Untitled_Note.11.resources/typescript - function types3.jpg]]

**function types quiz**

![[./_resources/Untitled_Note.11.resources/typescript - function types quiz.jpg]]
