---
---
**Javascript arrays**

* if you insert a value into an otherwise empty array, the indices before that value are considered non-existent by the language 
* in other languages you could not do this, but JS alows it
* the keys of the array are the arrays' indices transformed into strings
* in JS, arrays are just considered objects, so when you enter **typeof whateverArray**,  you get **'object'** returned
	* the keys of they array \[4, 5\] are considered the indices of the array members, which are also converted to strings - **\['0', '1'\]**
	* **Object.keys(\['a', 'b', 'c'\]) -->** **\['0', '1', '2'\]**
	* arrays in JS are allowed to be **sparse**, meaning you can insert a value at a certain index, and the indices before that are considered just nonexistent 
* ![[./_resources/Untitled_Note.16.resources/javascript - array indices.jpg]]
