---
---
SQL injection notes

	**SQL Injection**
		![[./_resources/SQL_Injection_Notes.resources/unknown_filename.png]]
		
		SQL injection allows an attacker to submit malicious SQL statements to a database via the regular form submission. Where a user would normally enter safe text, an attacker submits SQL that will cause a database to provide confidential information or simply delete data.
		
		**Examples of attacks**
			**Retrieve hidden data** – a SQL query is modified to return additional results
			
			When visiting a site, a query is made to a database in order to retrieve relevant results
			
			The following URL entry can effectively call all entries under the “Gifts” category
			
			[https://insecure-website.com/products?category=Gifts'--](https://insecure-website.com/products?category=Gifts%27--)
			
			As the two dashes at the end of the query act as comments in SQL, they effectively comment out whatever remaining part of the query would have limited the number of Gifts displayed, thus displaying potentially sensitive data
			
			The following query will result in the display of all products in all categories
			
			[https://insecure-website.com/products?category=Gifts'+OR+1=1--](https://insecure-website.com/products?category=Gifts%27%2BOR%2B1=1--)
			
			Because we’re telling the database to either return the Gifts or 1=1, the database returns all Gifts
			
			**Subverting application logic** – where you can change a query to interfere with an application’s logic
			
			the following query will return the user whose username is ‘administrator’ and logs in the attacker. The query removes the password check from the WHERE clause
			
			SELECT \* FROM users WHERE username = 'administrator'--' AND password = ''
			
			On an actual website, you don’t even need to alter the URL, but adding a small change to the **username** field to make it an SQL statement works well: 
				![[./_resources/SQL_Injection_Notes.resources/unknown_filename.1.png]]
				
			The above will allow us to log into the site as the administrator regardless of what we use as the password, because the SQL statement comments out the password value
			
			**UNION attack** – data is retrieved from multiple database tables
				the reason for performing a UNION attack is to be able to retrieve the results from an injected query
				
				the use of the UNION keyword allows additional SELECT statements to be made, thus data from other tables to be appended to what is returned 
				
				**UNION SELECT username, password FROM users--**  will return all usernames and passwords along with whatever other legitimate data was requested
				
				an example of a UNION attack on a site would look something like the below (click to enlarge).  Note the query written after the **filter** keyword
					![[./_resources/SQL_Injection_Notes.resources/unknown_filename.4.png]]
					
					the reason NULL is used in the injection attack is because data types between the injected values and original values must match.  NULL is convertible to commonly used data types and thus increases the attack's likelihood of success
					
					interesting data will likely be in string format, so look through the original query results for data types that are compatible with string data
					
				**Finding Columns Containing Text**
					**first** we need to find out which column contains text before we try to insert anything
						use the above UNION techniques to find out which column contains any text at all
						
						when you find out one column does contain text, then you can insert your preferred text in that column
							![[./_resources/SQL_Injection_Notes.resources/unknown_filename.5.png]] 
							
				**SQL injection UNION attack, retrieve data from other tables**
				
			**Examining the database** – data regarding the version and structure of the database is extracted
				code such as **SELECT \* FROM information\_schema.tables** will give you a list of all the database tables
				
			**Blind SQL injection** – the results of a query you control are not returned in the application’s responses
				even though there is no explicit data being returned with the query, an advanced attacker can still use blind injections to
					change behavior in an application with subtle changes to a query
					
					infer the truth of a certain condition by observing a time delay in the response to a query
					
					using [OAST](https://portswigger.net/burp/application-security-testing/oast) techniques, trigger and out-of-band network interaction 
						OAST stands for Out-of-band Application Security Testing
						
						 uses external servers to see otherwise invisible vulnerabilities
						
						lots more written 
						
	**manual detection of SQL injections**
		 submit a single quote - ' - and see if there are errors or anomalies
		
		submitting a SQL-specific syntax which evaluates to the base (original) value of the entry point, and to a different value, and looking for systematic differences in the resulting application responses
		
		submitting Boolean conditions and seeing if there are changes in the application response
		
		submitting payloads meant to trigger time delays in an application's response
		
		submitting OAST payloads meant to trigger out-of-band network interactions
		

	**SQL injection in different parts of the query**
		most injection attacks take place when using the WHERE clause of a SELECT, but any part of the query; the most locations for an injection are:
			UPDATE
			
			INSERT
			
			SELECT, along with the ORDER BY clause
			
	**Second-Order SQL injection**
		first-order injections arise when an application takes input via an HTTP request and in processing that request incorporates the input of the SQL query in an unsafe way
		
		**second-order (stored SQL injection)** has the application still take an HTTP request but store it for later, usually in a database. Later when another, different HTTP request is handled the previously stored request is process and that stored SQL query is handled in an unsafe way
		
		![[./_resources/SQL_Injection_Notes.resources/unknown_filename.2.png]]
		
		second-order injections are often made possible when devs initially try to guard against injections by storing the data safely; the data is later processed and is assumed to be safe, but is ultimately handled in an unsafe way
		
	**Database specific factors**
		core features of SQL are implemented across platforms, thus certain injections also work across platforms
		
		this being the case, it's important to be aware  of small differences between databases in order to fully exploit them
		
	**How to prevent SQL injection**
		using **parameterized queries** **(**aka **prepared statements)** rather than string concatination within a query
			rather have user input directly concatinated into the query using the "+" sign, a statement that the user input cannot alter is prepared and then sent off
				![[./_resources/SQL_Injection_Notes.resources/unknown_filename.3.png]]
