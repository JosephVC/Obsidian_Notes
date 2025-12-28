---
---
**Template literals**

* using backticks (shift+tilde) is equivalent to single quotes in javascript \`hello\` === 'hello'
* the importance of using backticks like this is that it allows you to interpolate the result of an expression into a string by using curly braces ${ } - this converts the value within the braces to a string
* **if you are using template literals you need to wrap it in backticks, as single quotes won't work**
	* **example:** ![[./_resources/Untitled_Note.15.resources/javascript-template literals.jpg]]
	
* You can also use template literals to create newlines more easily
	* ![[./_resources/Untitled_Note.15.resources/javascript-template literals - newlines.jpg]]
	* if you don't want the included whitespace, then you can use the npm dedent module
