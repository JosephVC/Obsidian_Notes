---
---
**What is SQL Injection?**The point wherein a web application using SQL can turn into SQL Injection is when user-provided data gets included in the SQL query.

**What does it look like?**Take the following scenario where you've come across an online blog, and each blog entry has a unique id number. The blog entries may be either set to public or private depending on whether they're ready for public release. The URL for each blog entry may look something like this:

<https://website.thm/blog?id=1From>

the URL above, you can see that the blog entry been selected comes from the id parameter in the query string. The web application needs to retrieve the article from the database and may use an SQL statement that looks something like the following:

**SELECT \* from blog where id=1 and private=0 LIMIT 1;**

From what you've learned in the previous task, you should be able to work out that the SQL statement above is looking in the blog table for an article with the id number of 1 and the private column set to 0, which means it's able to be viewed by the public and limits the results to only one [match](http://match.As).

[As](http://match.As) was mentioned at the start of this task, SQL Injection is introduced when user input is introduced into the database query. In this instance, the id parameter from the query string is used directly in the SQL query.  Let's pretend article id 2 is still locked as private, so it cannot be viewed on the website. We could now instead call the URL:

 [https://website.thm/blog?id=2;--](https://website.thm/blog?id=2;--Which)

[Which](https://website.thm/blog?id=2;--Which) would then, in turn, produce the SQL statement:

SELECT \* from blog where id=2;-- and private=0 LIMIT 1;

**The semicolon in the URL signifies the end of the SQL statement, and the two dashes cause everything afterwards to be treated as a comment**. By doing this, you're just, in fact, running the query:

**SELECT \* from blog where id=2;--**

Which will return the article with an id of 2 whether it is set to public or not.

This was just one example of an SQL Injection vulnerability of a type called In-Band SQL Injection; there are 3 types in total In-Band, Blind and Out Of Band

**In-Band SQL Injection**

In-Band SQL Injection is the easiest type to detect and exploit; In-Band just refers to the same method of communication being used to exploit the vulnerability and also receive the results, for example, discovering an SQL Injection vulnerability on a website page and then being able to extract data from the database to the same page.

## **Error-Based SQL Injection**

This type of SQL Injection is the most useful for easily obtaining information about the database structure as error messages from the database are printed directly to the browser screen. This can often be used to enumerate a whole database. 

## **Union-Based SQL Injection**

This type of Injection utilizes the SQL UNION operator alongside a SELECT statement to return additional results to the page. This method is the most common way of extracting large amounts of data via an SQL Injection vulnerability.
