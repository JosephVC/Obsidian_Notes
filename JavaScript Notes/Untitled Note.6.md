---
---
**Array Destructuring**

originally, working with arrays in JS was tough and cumbersom, but destructuring makes the whole process much cleaner and easier

the array itself will have a structure where certain values go with certain indices; de-structuring allows us to unpack (destructure) and get the individual values

![[./_resources/Untitled_Note.6.resources/javascript - basic array destructuring.jpg]]

![[./_resources/Untitled_Note.6.resources/javascript - basic array destructuring2.jpg]]

the keywords **let**, **const** and even **var** can be used in destructuring 

destructuring allows you to skip over array indices in what is called sparse array destructuring 

but, if an object has too few indices, then we get **undefined**  returned
![[./_resources/Untitled_Note.6.resources/javascript - basic array destructuring - too few i.jpg]]

You can use rest variables to further refine  your destructuring, so you don't have to burn time noting every single variable

![[./_resources/Untitled_Note.6.resources/javascript - array destructuring - rest arrays.jpg]]

like with using regular rest parameters, the you'll get an **error** if the rest param comes first

you can also use destrucuring to pull individual items out of an object

![[./_resources/Untitled_Note.6.resources/javascript - array destructuring - rest arrays - i.jpg]]

**MORE DESTRUCTURING!!!**

Go back to how arrays are destructured 

![[./_resources/Untitled_Note.6.resources/javascript - array destructuring.png]]

the above is taking the 0th element of the array and making it the value of **firstName**

so, **firstName == names\[0\]**

You can also destructure **objects**

![[./_resources/Untitled_Note.6.resources/javascript - object destructuring.png]]

Trying to destructure a **null** or **undefined** will throw an error, or if the key doesn't exist, we get **undefined**

![[./_resources/Untitled_Note.6.resources/javascript - null or undefined destructuring.png]]

![[./_resources/Untitled_Note.6.resources/javascript - destructuring without a key.png]]

We can supply default values when destructuring, but these **don't override pre-existing values**

![[./_resources/Untitled_Note.6.resources/javascript - destructuring with default values.png]]

**Rest values** can also be used

![[./_resources/Untitled_Note.6.resources/javascript - destructuring with rest values.png]]

![[./_resources/Untitled_Note.6.resources/javascript - destructuring with rest values 2.png]]

![[./_resources/Untitled_Note.6.resources/javascript - destructuring to apply values.png]]

Destructuring can also be used with getters

![[./_resources/Untitled_Note.6.resources/javascript - destructuring with getters.png]]

Getting deeper into how objects are deconstructed, below is an example of nested arrays and how to pull data from such arrays

![[./_resources/Untitled_Note.6.resources/javascript - deconstruct - nested arrays.png]]

Nested objects can also be matched:

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - nested values.png]]

a thing to remember her is that the **address** noted above does not actually contain a value, but only exists so we can access the actual address in this case, which is the **city** variable.  Calling **address** by itself will cause an error

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - nested values - error.png]]

To get access to the actual address, we need to call the **city** variable explicitly 

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - nested values - ask f.png]]

A trick with destructing is to use multiple dots rather than the above brackets to pull values out of what you want.  Also, when given multiple values, iterate through them with a **for** loop

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - iterate through list .png]]

Here is another example of extracting data with destructuring

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - extracting values.png]]

Another example, like the above using dot notation to access values, can use **for** loops, as well as **try/catch** 

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - for loop, try-catch l.png]]

You can also use destructuring within function definitions

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - within function defin.png]]

Rest functions can also be used with destructuring 

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - using rest functions.png]]

![[./_resources/Untitled_Note.6.resources/javascript - destructuring - misc..png]]
