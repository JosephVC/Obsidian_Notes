---
---
**SQL Injection**

You can build the INSERT statement to be more robust

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement.png]]

the problem with the above code is that it allows someone to insert whatever code they want as an email, taking advantage of your system 

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - injecting faulty code.png]] 

The above kinds of coding errors are what allow the nefarious **SQL injection** vulnerability 

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - injecting faulty code 2.png]]

the key here is the use of the single quote - ' - that closes the string, which allows the inserted email address to be inserted as normal SQL code 

also, the whole reason there is a comment the end is to allow for there to not be a syntax error at the end of the SQL statement; we are adding what would normally be an unnecessary single quote and closing parens.  

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - mistmatched quote marks.png]]

One of the best examples of this is the bobby tables example:

In the below, we first wrap what we are passing to **register()** in double quotes, because it is the string we are trying to inject.  If we weren't trying to inject anything and just wanted add the name "Robert" we'd surround the name with double quotes as so - **register("Robert")**.  within that string, we are adding **within the single quotes** our DROP TABLE command, which is ended with a comment. 

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - bobby tables.png]]

rather than drop tables, someone could become administrator of a system

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - change admin.png]]

Here's another example, but with another user inserted in

![[./_resources/Untitled_Note.6.resources/sql - INSERT statement - change admin and innocent.png]]
