---
---
**Javascript Arrays**

the following is a basic quiz on whether an array is empty or not.  The solution is the use the JS bias towards truthiness - like Python -  and if that fails return a **false** output

![[./_resources/Untitled_Note.resources/javascript arrays - isEmpty quiz.png]]

**Accessing Elements**

this quiz required the return of element **i** within the array **arr**.  what made the problem more tricky was that there could be arrays that were empty, thus needing the test of **!(arr.length)** - whether there is no length to the array - to check if there was anything at all to return.  We also need to test against when i is either greater than the length of the array or negative

![[./_resources/Untitled_Note.resources/javascript arrays - element access quiz.png]]

**Element Assignment** 

Here we assign the value of zero to the 1 index the given array.  the reason **null** is returned is in case the first first element of the array is already a zero.  The simplest way to do this it take advantage of the JS bias towards truthiness and simply test if the array has any length at all, and if so insert a 0 into the 1st element of the array.  

![[./_resources/Untitled_Note.resources/javascript arrays - element assignment quiz.png]]

**The Stack**

JS arrays are like a stack, where you **.push** a value onto the stack to append to the back (top) of it

![[./_resources/Untitled_Note.resources/javascript arrays - push.png]]

simply pushing an element to an array will return the length of the array

the **.pop()** method does the opposite of **.push()** in that it removes the back (top) item from the array.  Rather than return the new length of the array, **.pop()** returns the value that was popped off the end

**Slice**

the **.slice()** method implicitly takes a **start** at the given value, and by default will continue slicing until the end of the array.  so **\[1,2,3\].slice(1)** returns **\[2,3\]**

you can explicitly set and **end** to the slice, **but remember it's not inclusive** , meaning the slicing will stop before the index you specify.  So **\[1,2,3\].slice(1, 2)** will only return **\[2\],** as it starts at index 1 and stops one short of index 2.  If you want to slice beyond the length of the array, the method will work until the very end of the array

If you try slicing indices that don't exists at all, then an empty array is returned

![[./_resources/Untitled_Note.resources/javascript arrays - slice nonexistant indices.png]]

**without arguments, .slice() will take all elements of an array**

to create a function that slices up to a certain element **n**, do as follows

![[./_resources/Untitled_Note.resources/javascript arrays - slice quiz.png]]

**slice()** can also return the copy of an array simply create a new variable equal to **original\_array.slice()**

**Concatenate** **(add to) arrays**

while other languages simply allow you to use a "+" to concatenate arrays, JS produces odd output when that is done

![[./_resources/Untitled_Note.resources/javascript arrays - concat with plus sign.png]]

To get more sensible ouput, use the **.concat()** method

![[./_resources/Untitled_Note.resources/javascript arrays - concat with plus sign.png]]

You can still **.concat** items that aren't arrays to other arrays, such as **\[1,2\].concat(3) == \[1,2,3\]**

 **.concat()** builds a new array without altering the original

![[./_resources/Untitled_Note.resources/javascript arrays - concat returns new array.png]] 

You could always set **a1.concat(a2)** to a new variable and call it in order to get the newly formed array

**Includes**

![[./_resources/Untitled_Note.resources/javascript arrays - includes.png]]

**New, Fill**

the **fill** method fills an array with a given value.  

**var foo = \[1,2,3\]**

**foo.fill('foo')**

**foo**

**\>\['foo', 'foo', 'foo'\]**

you can create an array of a given size by using **let size = 5;**  **new Array(size).fill('foo')**

![[./_resources/Untitled_Note.resources/javascript arrays - fill arrays.png]]

![[./_resources/Untitled_Note.resources/javascript arrays - fill arrays quiz.png]]

**For Each**

**For each** is a way for us to iterate through an array and perform operations on the contents

![[./_resources/Untitled_Note.resources/javascript arrays - forEach.jpg]]
