---
---
**Multiple statements**

we can use the semicolon to separate statements in SQL.  This results in only the last statement being returned.  While just the last statement is returned, that statement sees the behavior of all the previous statements.

rather than repeatedly typing **exec(\`....\`)** for every statement we want to use, we only need to watch 

**![[./_resources/Untitled_Note.8.resources/unknown_filename.png]]**

**Keep in mind** bind parameters and multiple statements can't be used at the same time with most SQL APIs

![[./_resources/Untitled_Note.8.resources/sql - no multiple statements with bind parameters.png]]
