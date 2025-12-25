---
---
**Referencing Other Tables**

in real databases, tables often refer to each other

you could reference the name of some user - for example - as part of another user or entity, but then you would have what amount to a bunch of nested tables and part of SQL's value is lost 

![[./_resources/Untitled_Note.7.resources/sql - reference other tables.png]]

![[./_resources/Untitled_Note.7.resources/sql - reference other tables 2.png]]

All the above can be combined together in JS

![[./_resources/Untitled_Note.7.resources/sql - reference other tables in JS.png]]

Rather than create tables for each cat name - sam\_cat, joe\_cat - we create a table with all the cats, and then let the owner's id guide us to the cat

This follows a basic design pattern, of **never allowing the application to alter the structure of the database; applications do not create or drop tables nor delete columns, but only updates create, updates, or deletes rows**

![[./_resources/Untitled_Note.7.resources/sql - reference other tables - find toy.png]]
