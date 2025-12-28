---
---
Functions 

**scoped:** Variable scope is created within functions, where variables defined within the function are visible and usable within that entire function **but not outside the function**

* even if a variable is defined within an if statement, the variable should still be local to that statement
	* it's too easy to declare a variable within the if statement and then accidentally use it outside that statement
* with **let,** the above problem was fixed in 2015; when using **let**, a variable isn't visible outside the given statement it's defined in
	* we can now define **foo** within an a statement and then another **foo** variable within another part of the function
		* this is called **shadowing** , where the inner **let foo** shadows the outer **let foo**
		
* these rules apply to any block of code within curly braces; whatever variables you define within curly braces only has scope within those curly braces
* **Constant variables**: if you assign a value to a variable you declared as constant, then you can't try and reassign a different value to that same constant variable

![[./_resources/Untitled_Note.17.resources/javascript-type-error.png]]

*  you can still mutate the value of a constant variable by using the **const**'s **push** method; you just can't assign an array variable to hold a new array
	* **const applies to the variable, rather than the value held by the variable;** this also means we can't define the same variable twice
	* we can use **let** to shadow **const** variables, though, and we can define the same const variable within different scopes
	* **prioritize using** _**let**_ **and** _**const**_ **rather than** _**var**_ **to define variables** 
	* you can use linters and plugins to force the use of let and const
		

* this means we can treat arrays as any other kind of object
