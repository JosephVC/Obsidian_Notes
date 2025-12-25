---
---
**Join Performance**

![[./_resources/Untitled_Note.1.resources/unknown_filename.png]]

the problem with the above is efficiency: if we have thousands of people, then our loop will get bogged down and take inordinate amounts of time to finish

this is called an **N+1** problem, where we do one person query the N (1,000) cat queries

We can optimize the above code by creating an **if** statement that tests whether a cat's owner\_id is equal to a person's id (that is, if a cat really belongs to a person); this is more efficient than just running through an entire list of cats to see if they belong to one person, and reduces our query to 2 people (in this case)

![[./_resources/Untitled_Note.1.resources/unknown_filename.1.png]]

There still is another problem, and that is with the nested loops in the middle of our code; on a large database, we are still stepping through each entry unnecessarily 

![[./_resources/Untitled_Note.1.resources/unknown_filename.2.png]]

SQL can make our code more efficient by restructuring our query 

![[./_resources/Untitled_Note.1.resources/unknown_filename.3.png]]

by restructuring our query per the above, we will limit the number of people the code looks at to just one person

If a database is set up properly, even tens of thousands of records can be whittled down with properly used keywords
