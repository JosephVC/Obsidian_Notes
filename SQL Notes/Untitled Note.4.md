---
---
**Foreign Keys**

Correctness is a big selling point for SQL databases, and one thing that allows for this correctness is the ability to set up constraints it makes no sense to violate to begin with

one way a wrench gets thrown into all this is where tables can reference each other using identifiers they should not have access to, such as when one table references another using an id it presumes the other has, but does in fact not have

![[./_resources/Untitled_Note.4.resources/sql - foreign keys.png]]

the id of the name within the  **person** database is getting confused with the owner\_id in the **cats** database,

the above problem can be solved by  using **foreign keys**

keys are columns that uniquely identify rows, so when you have one column that references another, it is referring to a **foreign** value

![[./_resources/Untitled_Note.4.resources/sql - foreign keys - PREFERENCES keyword.png]]

the **REFERENCES** keyword allows us to specify which database we want to look at for an **id**

![[./_resources/Untitled_Note.4.resources/unknown_filename.1.png]]

Here, we are allowed to enter an owner with an id of 100 and their cat - linked to the same id

![[./_resources/Untitled_Note.4.resources/unknown_filename.png]]

what we are  not allowed to do is enter a cat with an id that does not have a corresponding owner id; no person has an id of 200, so no pet entry using that id number is allowed

![[./_resources/Untitled_Note.4.resources/unknown_filename.2.png]]

because the **id field** between owners and cats is shared, we can't just go changing one 

![[./_resources/Untitled_Note.4.resources/unknown_filename.3.png]]

Again, because the two tables are linked via their id, we cannot just delete an entry from one

![[./_resources/Untitled_Note.4.resources/unknown_filename.4.png]]

this above is allowed, because we delete the cat entry which is tied to the person entry

another term to describe the above is **referential integrity** 

references are made to other tables in such way as the data of one table helps keep the other correct

we can still update and delete values

![[./_resources/Untitled_Note.4.resources/unknown_filename.5.png]]

initially, there were two separate owner id's
Keanus' owner\_id was updated to 100, meaning he belonged to Amir along with Ms. Fluff
we can safely delete Betty as no cat belongs to her

all the effort going into these schemas saves us a shit ton of work later on

data that is in a faulty schema can **leak**, when it is no longer effectively protected by being referenced by another row, as in the above example

![[./_resources/Untitled_Note.4.resources/unknown_filename.6.png]]

**Foreign Keys Quiz**
**![[./_resources/Untitled_Note.4.resources/sql - foreign keys quiz.png]]**
