---
---
**Simple Joins**

as we have foreign keys to allow us to relate data in one table, we might as well figure out how to combine data across tables; **join** allows this

One way to think of joins is as like two nested loops with a filter

![[./_resources/Untitled_Note.resources/unknown_filename.png]]

* for each person in the cats table
	* for each cat in the cats table
		* if the ON condition is true for this person and this cat
			* return a row with the column from this person and this cat

![[./_resources/Untitled_Note.resources/unknown_filename.1.png]]

as we are joining two simple tables, with two columns each, we end up with four total columns after the JOIN; if we had 100 people and 100 cats we would have 10,000 rows

You can refine what the JOIN returns by using AS

![[./_resources/Untitled_Note.resources/unknown_filename.2.png]]

the order of tables does not change if you JOIN cats before people or vice versa

there are two cases in which the order does matter:

* **query optimization**: a database may be optimized to do certain joins badly, thus you would want to tune your JOIN to fit how the database is optimized 
* **duplicate column names**: when joined tables have duplicate column names, the last table in the JOIN wins; try tuning the query to more fully express the data
* ![[./_resources/Untitled_Note.resources/unknown_filename.4.png]]
* it might be useful to tune your query with AS to produce more coherent results in cases where you want all the columns to show up even when some have duplicate names
* ![[./_resources/Untitled_Note.resources/unknown_filename.3.png]]

we can also tune the queries with WHERE to return more specific results

![[./_resources/Untitled_Note.resources/unknown_filename.5.png]] 

![[./_resources/Untitled_Note.resources/unknown_filename.6.png]]

an important note is that when A has two instances of B attached to it, it will return two separate rows rather than combine the two Bs together:

![[./_resources/Untitled_Note.resources/unknown_filename.7.png]]

If  you don't structure your query well enough,  you can get values conflated, and make it appear as if certain Bs belong to an A even when they don't

![[./_resources/Untitled_Note.resources/unknown_filename.8.png]]

![[./_resources/Untitled_Note.resources/unknown_filename.9.png]]

![[./_resources/Untitled_Note.resources/unknown_filename.10.png]]

![[./_resources/Untitled_Note.resources/unknown_filename.11.png]]
