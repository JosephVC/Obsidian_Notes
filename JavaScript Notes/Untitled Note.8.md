---
---
**Rest Parameters**

Rest parameters allow a function to take multiple arguments at  once by simply adding three dots - no spaces - before the parameter name **...parameters**

**functions using rest parameters return an array of values**

![[./_resources/Untitled_Note.8.resources/javascript - basic rest parameters.png]]

![[./_resources/Untitled_Note.8.resources/javascript - basic rest parameters2.png]]

You can use what are called **positional parameters** to further expand the sort of arguments you provide a function and how those arguments interact; the positional parameters must be used  **before** the rest parameters, though

![[./_resources/Untitled_Note.8.resources/javascript - rest parameters using positional para.png]]

in the above, we're not just adding all the parameters together, but are adding the first positional parameter to whatever is in the **...numbers** parameters

there are rules regarding combining positional parameters and rest parameters

*  you cannot put the positional parameter after the rest parameters
	* 
* you cannot have multiple rest parameters, as there would be no way for the JS Virtual Machine to tell which arguments go with which rest parameter
	* 

If you have an array of values already created, you can turn that variable into a rest parameter simply by adding the three dots

An example of this would be when you define an array of values you then want those values passed into a function; just use rest parameters to pass the values\\

![[./_resources/Untitled_Note.8.resources/javascript - rest parameters3.png]]

![[./_resources/Untitled_Note.8.resources/javascript - rest parameters to sum numbers.png]]
