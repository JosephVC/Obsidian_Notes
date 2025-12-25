---
---
**Tuples**
![[./_resources/Untitled_Note.5.resources/typescript - tuples.jpg]]

**Tuples quiz**
![[./_resources/Untitled_Note.5.resources/typescript- tuples quiz 1.png]]

![[./_resources/Untitled_Note.5.resources/typescript- tuples quiz 2.png]]
So, in the above, we are given an array of arrays.  
The first thing we need to do is alter what argument our function takes
    We give the function an argument that is an array containing a string at the 0th index and a number at the 1st index **but what does the second bracket mean?**
Next, we create an empty array, but specify that it contains strings
even though the forEach hasn't been introduced at this time, there seems to be no other way other than to use a forEach to step through the array 
    so, for each sub array element in the main array given as argument, we push what portion of the element is a string to our **result** array, which we specified above can only contain strings
