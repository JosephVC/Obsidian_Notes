---
---
**dropping tables and columns**

the **DELETE** keyword simply removes the data but leaves the table intact

to delete both the table and its data, we need **DROP**

after a table is dropped,   trying to access it results in an error

![[./_resources/Untitled_Note.16.resources/sql -DROP.png]]

The difference between dropping and delete comes down to whether you are altering the data of a database or its structure.  DELETE only removes data, but keeps the structure intact in so far as the table itself is still there. DROP alters both, as the table and its data are no longer there.   More advanced uses of **DROP** allow you to DROP individual portions of a table without nuking the whole thing.
