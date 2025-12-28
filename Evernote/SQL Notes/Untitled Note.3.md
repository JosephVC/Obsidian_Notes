---
---
**Constraint Analysis**

what if the foreign key we reference is null?

the above might actually be useful where we have some instances where we want null values, such as when values for a user table might need to be null due to not entering a discount code (or something)

the trick is to make sure values and their references match up in a way that does not break the database

![[./_resources/Untitled_Note.3.resources/unknown_filename.png]]

if value B references A, then you can't have B referencing a value that does not exist

it may be possible that both A and B are empty

![[./_resources/Untitled_Note.3.resources/unknown_filename.1.png]]

If A does exist, b can of course reference it

There  may be certain situations where B can only reference A once, and only one instance of B can reference A

![[./_resources/Untitled_Note.3.resources/unknown_filename.3.png]]

![[./_resources/Untitled_Note.3.resources/unknown_filename.2.png]]

the examples above are waht are called a **one to one** relationship; B usually refers to one A, and an instance of A can usually refer to one B (unless B represents a series of comments by one user A, in which A would have multiple instances of B)

![[./_resources/Untitled_Note.3.resources/unknown_filename.4.png]]

Here are some more examples

![[./_resources/Untitled_Note.3.resources/unknown_filename.5.png]]

![[./_resources/Untitled_Note.3.resources/unknown_filename.6.png]]
