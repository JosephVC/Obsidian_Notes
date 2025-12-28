---
---
**Type Unions**

when working with types, you can use a union - the pipe | symbol - to declare that multiple types may be acceptible

![[./_resources/Untitled_Note.4.resources/typescript- basic type unions.png]]

Below are examples of type unions being used with the **concat** method

![[./_resources/Untitled_Note.4.resources/typescript- type unions with concat.png]]

![[./_resources/Untitled_Note.4.resources/typescript- type unions with concat - real concat.png]]

In the above, we can combine two arrays or an array with a single number, like the traditional .concat() method

*     create the argument so that it accepts a number array, and the create a union where either a number array or single number is accepted
* create another array that simultaneously checks with the **a2** array is actually an array **and** then makes the above **a2** argument into an array - the **\[a2\]**
* return whatever is contained in a1 with whatever is contained in a2
* if there are strings passed as arguments, then we get a type error

**if we create a function that takes a union of WHATEVER | WHATEVER, we need to feed both whatevers when we invoke an instance of that function**

![[./_resources/Untitled_Note.4.resources/typescript- type unions - type error.png]]

Here is an example using **map** 

![[./_resources/Untitled_Note.4.resources/typescript- type unions -map example.png]]B 

* Here we create a **User** variable who accepts a string 
* create a function **userName** that accepts either a variable **u** as an array of **Users** or a single **User**, then returns a string
* in our return statement we test if **u**  is an array, and if so then map that value to the name key defined in **User** 
* finally return an array of names
* note that we need to feed arguments with the key of "name" otherwise we get a type error, as we originally did not set the function **userNames** to accept "email", but only "name" as **userNames** is based on our **User** variable, which only takes "name" as a key

**Stringify Quiz**

This quiz is an extension of what we learned above, so belongs in this section.  All we have to do is define an argument that takes all the necessary parameters and returns a string, by using the toString method on whatever the arg is.

![[./_resources/Untitled_Note.4.resources/typescript - stringify quiz.png]]
