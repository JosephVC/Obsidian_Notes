---
---
**Comparing with NULL**

NULL is kind of a blunt tool.  For example, if you compare anythng with NULL, you get NULL back

![[./_resources/Untitled_Note.14.resources/sql - NULL with math operations.png]]

using NULL in any sort of comparison will only result in NULL

there is also **IS NULL** and **IS NOT NULL** to help with comparisons (keep in mind that **true** and **false**  are 1 and 0, respectively 

these values are good to test against when using the **WHERE** keyword

![[./_resources/Untitled_Note.14.resources/sql - IS NULL - IS NOT NULL .png]]

In the above examples, both **1 and 0**  are references to true and false

![[./_resources/Untitled_Note.14.resources/sql - IS NULL - IS NOT NULL used in WHERE.png]]

how NULL will work in practice will vary from database to database, but the above are generally applicable
