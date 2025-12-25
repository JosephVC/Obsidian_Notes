---
---
**Basic Tables**

![[./_resources/Untitled_Note.22.resources/sql - basic table.jpg]]

![[./_resources/Untitled_Note.22.resources/sql - basic SELECT.jpg]]

It's probably worth remembering part of the above, where executing a SELECT statement return **an array of objects**

![[./_resources/Untitled_Note.22.resources/sql - basic INSERT.jpg]]

![[./_resources/Untitled_Note.22.resources/sql - basic SELECT -2.jpg]]

A table can have as many columns as the user wants; SQLite allows up to 2000 and can be configured to allow a max of 32, 767.

It's also good to remember the name of the field you want to create goes before the type,  such as: **email TEXT, name TEXT** in the above screenshot

Statements that try to retrieve data that's not there will simply return empty brackets

**SQL keywords ignore case for keywords, but not for the individual values held**

**![[./_resources/Untitled_Note.22.resources/sql - case sensitivity.jpg]]**

**Trying to do any work on a column that does not exist will result in an error.**

**Basic Column Types**

SQL supports other data types, of course

* **INTEGER** is any positive or negative whole number
* **REAL** is any real number, stored as a double-precision floating point number

queried numbers are returned as numbers, not strings

You create a table with the above values the same way you would with strings

![[./_resources/Untitled_Note.22.resources/sql - create with integers.png]]

while the main types worked with in these notes are TEXT, INTEGER, and REAL, databases like PostgreSQL support up to 42 unique data types.  The reason for all these unique types is that they allow automatic error correction, where entering the wrong value isn't allowed by the program.  An example is the data type for IP addresses: '123,abc' would never be allowed to be entered in the first place, so data errors are kept lower by having these specific data types.

**Selecting Columns**

We can select columns from a database without using \*, which selects everything

![[./_resources/Untitled_Note.22.resources/sql - selecting columns.png]]

of course, if you try to select a column that isn't there, you get an error

![[./_resources/Untitled_Note.22.resources/sql - selecting nonexistant data.png]]

**Select Where**

there's been a lot of talk about columns in SQL, but there are also **rows** 

to select a certain row, you use the keyword **where**

**\= sign is standard use, rather than '==' or '==='**

![[./_resources/Untitled_Note.22.resources/sql - selecting using WHERE and SELECT.png]]

![[./_resources/Untitled_Note.22.resources/sql - selecting using WHERE and SELECT 2.png]]

You can also use the standard set of comparison operators in addition to the equal sign

here is an example of returning multiple entries.  **these entries have to be from top to bottom in this case; 'betty.j' has to come before 'betty.k'**

![[./_resources/Untitled_Note.22.resources/sql - selecting multiple entries.png]]

You can also used logical operators like **AND, OR, NOT, etc.**

![[./_resources/Untitled_Note.22.resources/sql - selecting multiple entries w-logical operato.png]]

You can use functions in your query as well 

![[./_resources/Untitled_Note.22.resources/sql - WHERE using function.png]]

**Lack of Type Enforcement in SQLite**

![[./_resources/Untitled_Note.22.resources/sql - lack of type checking .png]]

![[./_resources/Untitled_Note.22.resources/sql - lack of type checking 2.png]]

**Null**

null is the absence of a value

when a column is allowed to be null, we say it's nullable

in most database programs, columns are nullable by default unless specified otherwise

![[./_resources/Untitled_Note.22.resources/sql - null.png]]

You may not need to explicitly say  column is nullable but it's nice to do so

a column like **login\_count INTEGER NULL** means the column can take either an integer value or a null value

![[./_resources/Untitled_Note.22.resources/sql - null and not null.png]]

there are real world cases where  null values come up

![[./_resources/Untitled_Note.22.resources/sql - null example.png]]

the problem here is that SQL databases will not allow you to change the NULL value in a database once it is already there, so there needs to be some other option to repair this damage

leaving the field capable of containing nulls just means we'll keep running into the problem

intentionally making up fake numbers to go into the NULL fields at least fills those fields with non-NULL data, but it also means we've inserted fake data into our own database

the best way to solve this error is not make it in the first place by making the phone\_number field **NOT NULL,** this way the user will get an error if they try entering a NULL value in the db

![[./_resources/Untitled_Note.22.resources/sql - NOT NULL example.png]]

**No Booleans**

In SQL, booleans are not recoginized.  Rather, 1 = true while 0 = false.   that being said, having a 0 as a value still produces output

![[./_resources/Untitled_Note.22.resources/javascript - booleans.png]]

**Updating Rows**

We can update existing rows with the **UPDATE** command, which by default will update **every row** in the table.  This means that we can replace all instances of a value at once

![[./_resources/Untitled_Note.22.resources/javascript - basic update.png]]

As we often may not want to change every instance of a row all at once, we can use **WHERE** to specify what fields to update

![[./_resources/Untitled_Note.22.resources/javascript - basic update with WHERE.png]]

![[./_resources/Untitled_Note.22.resources/javascript - basic update with WHERE 2.png]]

**Inserting Multiple Rows**

the insertion of large numbers of rows can be resource intensive 

to reduce the cost of that insertion we put multiple rows of data after the **VALUES** keyword

![[./_resources/Untitled_Note.22.resources/sql - insert multiple rows.png]]

this doesn't mean you can insert  null values in NOT NULL fields

![[./_resources/Untitled_Note.22.resources/sql - insert multiple rows NOT NULL.png]]
