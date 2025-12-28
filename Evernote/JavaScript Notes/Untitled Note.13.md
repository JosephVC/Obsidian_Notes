---
---
* **Is NaN**
	* any time you have something **undefined - 1**, JS will pop out Nan
	* any operation that includes NaN will also produce NaN
	* NaN is the only value in JS that is not equal to itself
	* you can use the **isNaN()** function to test if something is NaN
		* this function **converts it argument to a number**, so it really does **isNaN(0+n)**
		* **therefor, Number.isNaN(NaN) returns true**
		
		* when you do **isNaN(undefined)** you get **true**
			* the exception is **Number.isNaN(undefined)**, which returns **false**
