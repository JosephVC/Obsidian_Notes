---
---
**Bind**

the keyword **this** refers to the object a function belongs to

so, if a variable **name** is within a function **user**, **this.name** refers to the **name** instance within **user**

scope rules for this are weird

**bind** is a method on the function itself, and it changes the scope of **this** whenever you use it

![[./_resources/Untitled_Note.10.resources/javascript-bind1.png]]

Bind basically allows you to play with scope, binding one function to another by extending scope. Keep in mind that to properly use **bind**, there needs to be a set of parens after what you've bound **\[but why, to hold other arguments\]**

![[./_resources/Untitled_Note.10.resources/javascript-bind2.png]]

bind can be used to extend the scope of a functions **this** keyword, which can still be useful provided what we want to extract is still provided within the scope of the object, in this case **address**

![[./_resources/Untitled_Note.10.resources/javascript-this keyword.png]]

the use of **bind** becomes more obvious in the below shot, where address has no access to the **this** within **addressString,** so we need to access the latter some other way

![[./_resources/Untitled_Note.10.resources/javascript-this keyword different scope.png]]

in the lower example, you can get the result  you want by using **bind** to change the scope of **this**, so that now the **this.city** and **this.country** are extended to **addressString**, and thus can be seen and used by **address**

![[./_resources/Untitled_Note.10.resources/javascript-bind within a function.png]]
