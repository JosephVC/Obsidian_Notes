---
---
**bind parameters** 

SQL would not be very useful if it could not be combined with JS 

the below is an example of using JS to access items in the SQLite database

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - basic.jpg]]

a potentially confusing thing in accessing database values is the use of the "**?**" symbol; this is actually a real symbol one uses to access values

I read the below as follows:

* create a table with id and name fields; the id field has to be an integer and not null while the name field has to be text
* insert the correctly formatted values into the table
* create a variable **users** which will select a name from the **users** **table** where the id is a certain value 
	* what value is that id? it is 1, noted by the \[1\]
* create a user amir, which will access the 0th element in the users table
* access the **name** field of the 0th element of the users table

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - question mark symbol.jpg]]

You can use multiple question marks to query multiple fields

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - multiple question mark sym.jpg]]

You can create a function where you look for a specific id as an argument, then create a variable that passes that id 

The above reads as follows:

* hey, we're looking for an id
* which id
* the id we just passed as an argument in the function

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - function to find id in tab.jpg]]

here's an example where we are looking for an id in a **users** table

again, **which id?**, the one being passed as an argument in **findUser**

Here is slightly more complex example where we want to return individual objects **rather than the whole array**

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - return user object from qu.jpg]]

in this case i return null if there is nothing there, which would be the case if id=100, which does not exist

the trick to getting this is realizing the **queryResult** is only going to have one user object, the **id**

because it only has one object, I can produce the right output by asking for the 0th element, which is all it has anyway

If we know a single parameter can come up multiple times in a query, we can reference it multiple times with **?1, ?2,** etc.

![[./_resources/Untitled_Note.9.resources/sql - bind parameters - multiple instance of bind .jpg]]

In this case, we know 'Wilford' will show up twice, so we tailor our query to look for whether that parameter = name and owner\_name

the reason we use **?1** twice is that parameter numbers start at 1, thus **?1** refers to the 0th bind parameter.  In this case we only have one, **Wilford**, but if we had more than one we'd need   **?2**

note that the query function **takes different names depending on the language you're using**

with **Python,** rather than use **exec,** we use **execute**
