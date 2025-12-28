---
---
**Unique Constraints** 

SQL will return an error if  you set a variable's value to UNIQUE   and try to pass that same variable the same value

![[./_resources/Untitled_Note.10.resources/sql - basic unique constraints.png]]

even if one field has a  UNIQUE constraint, if you enter it for one value  you'll still get an error

![[./_resources/Untitled_Note.10.resources/sql - basic unique constraints 2.png]]

to fix this, just put UNIQUE constraints on both values.  The problem with this is how people with unique emails might have the same name, or even part of their email's domain name might be the same, thus throwing an error

Now what we have to do is test whether the name AND email are the same

![[./_resources/Untitled_Note.10.resources/sql - basic unique constraints 3.png]]

![[./_resources/Untitled_Note.10.resources/sql - UNIQUE contraints 2.png]]
