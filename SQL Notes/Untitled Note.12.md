---
---
**Selecting Expressions From Tables**

sometimes you need to alter what is returned from a SELECT statement without actually altering the value in the table

we can do this in SQL with the double pipe (||), which in SQLite means "concatinate" but in most other languages means OR

![[./_resources/Untitled_Note.12.resources/sql - selecting expressions from tables - basic.png]]

this way, we can add onto the values being returned without actually changing anything in the database table

there is another way to use selections combined with comparison operators, which in SQL include the BETWEEN operator

![[./_resources/Untitled_Note.12.resources/sql - selecting expressions from tables - BETWEEN .png]]

keep in mind that the **AND in SQLite does not have anything to do with the regular AND (&&), but is part of BETWEEN, so is really like BETWEEN . . . AND . . .**

stuff like the above are part of the SQL language itself, which has 760 different keywords rather than under 100 for JavaScript.  It can do this because it does not need to rely on other libraries (like npm) for keywords or functions.  

![[./_resources/Untitled_Note.12.resources/sql - selecting expressions from tables - exercise.png]]
