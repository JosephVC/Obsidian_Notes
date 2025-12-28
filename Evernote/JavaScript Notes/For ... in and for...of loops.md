---
---
**For ... in loops**
 the **for . . . in** loops iterate over an objects **keys** (but not its **values**)

* given the above behavior of arrays, if  you us the **for . . . in** loop over an array where 'foo' was inserted at index 3, you'll get an array where the first three elements are considered **undefined**
* given the ways arrays are treated in JS, just going through popping out keys can cause odd bugs, so the **for . . . in** loop was developed 
	

**For . . . of loops**

* **for . . . of** loops iterate over the **values** in an array **NOT AN OBJECT/DICT** rather than the keys
* given how JS arrays are allowed to be sparse, the values up to a given index are considered undefined 
* this ends up working like other **for** loops in Python
* ![[./_resources/For_..._in_and_for...of_loops.resources/javascript - for of loop on an array.jpg]]

You can use for... of to use an object to iterate over another object:
![[./_resources/For_..._in_and_for...of_loops.resources/javascript - fucking for of problem.jpg]]

Because you can't use for...of to iterate over the **obj** variable - it's not considered iterable - you need to iterate over the keys, the push those values the empty array
this problem was tricky, as the author only implicitly showed you how to to **bracket the key of each value  you wanted**

as the **for...of** loop steps through the array, it returns **'c', 'b', 'c';** the values being pushed are the corresponding values in **obj** of the those letter values 

There are also **Objects.keys** and **Objects.items** in addition to **Objects.values** you can use to gain the values out of an object

If you were to iterate over a string, then the output would be the contents of the string, but separated out between the brackets: 
![[./_resources/For_..._in_and_for...of_loops.resources/javascriptf- for loops over chars.jpg]]
