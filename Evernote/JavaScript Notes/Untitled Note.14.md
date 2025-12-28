---
---
**Accessors in object literals - setters and getters**

* Here are some basic object literals:
	* ![[./_resources/Untitled_Note.14.resources/javascript object literal.jpg]]
		
* javascript allows you to give these objects dynamic properties, by using a function
	* ![[./_resources/Untitled_Note.14.resources/javascript object literal with function.jpg]]
	
* **getters** are the formal name of what we are using above 
* ![[./_resources/Untitled_Note.14.resources/javascript getters.jpg]]
	
* **setters** write to objects
	* writing to an object's key replaces whatever value is at that key
	* setter properties contain functions, with the one value being written to the key
		
	* ![[./_resources/Untitled_Note.14.resources/javascript setters.jpg]]
		
	* you can see how the setter just takes over the value of newName, which is then assigned to - and takes over - teh value of realName which was set above
		* because of this, when we set user.name = 'Betty' it overtakes 'Amir' as the value of realName
		* if user.name was not set to 'Betty', the result would be **undefined**
		* the **newName** in **set name**  is effectively your variable
* ![[./_resources/Untitled_Note.14.resources/javascript getters and setters.jpg]]
	* One way to consider the above is to see the getter as getting a blank slate of a certain shape, ready for you to provide a name, and making sure that it returns a name
		* the setter is built to fill that shape
			* in this case, our shape is that of a name, and we slap a label on in named newName
				* as we create a new name, 'Betty', per the rules set above it gets appended to the list of names
* **Quiz answers**

![[./_resources/Untitled_Note.14.resources/javascript-review1.png]]

![[./_resources/Untitled_Note.14.resources/javascript-review2.png]]

![[./_resources/Untitled_Note.14.resources/javascript - shorthand properties.jpg]]
