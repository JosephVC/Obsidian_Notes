---
---
**Recognize Text**

the need for primary keys in SQL is because, if the same entry is entered in different fields, it can make adequate recovery of records more difficult

![[./_resources/Untitled_Note.17.resources/sql - need for primary keys.jpg]]

to get around this problem, each value can be assigned a numerical  ID; this makes referencing rows easier

![[./_resources/Untitled_Note.17.resources/sql - primary keys - id field .jpg]]

 we can, though, run into the same problem as before if different entries are assigned the same ID.  this is where the **primary key**  comes in

in terms of databases, a **key** refers to at least one column that is unique; declaring a value a **primary key** automatically sets that value as UNIQUE  and usually NOT NULL

* So, in a variety of ways, creating a **primary key** column prevents insertion of duplicate values

![[./_resources/Untitled_Note.17.resources/sql - primary keys - no duplicates.jpg]] 

the above is an example of how primary keys do not allow duplicates

**in SQLite, primary keys are nullable**,  

**![[./_resources/Untitled_Note.17.resources/sql - primary keys - nullable primary keys.jpg]]**

most primary keys in SQL are **auto-incrementing**, meaning you don't even need to specify the name "id" when creating the table

![[./_resources/Untitled_Note.17.resources/sql - primary keys - auto-incrementing primary key.jpg]]

if you specify a value needs to be **INTEGER PRIMARY KEY** then SQL will realize that the next value should be an increment rather than null

![[./_resources/Untitled_Note.17.resources/sql - primary keys - auto-incrementing primary key.jpg]]

**IF YOU TRY TO SET TWO DIFFERENT VALUES AS PRIMARY KEYS, IT WILL CAUSE AN ERROR**
