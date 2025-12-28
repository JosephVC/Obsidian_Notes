---
---
* the goal is to log into the account of Carlos, given that all we know is his email: [carlos@carlos-montoya.net](mailto:carlos@carlos-montoya.net)
* we have our own account, the username/password being **wiener/peter**
* we use the credentials directly above to log in, with traffic being intercepted and forwarded via Burp Suite
* When going to “My account” up in the corner, one noticeable thing is the session cookie that pops up in Burp
	* ![[./_resources/Web_Security_Academy_–_Authentication_bypass_via_Oauth_implicit_flow.resources/image.png]]
* after several forwards, the session cookie seems to change
* ![[./_resources/Web_Security_Academy_–_Authentication_bypass_via_Oauth_implicit_flow.resources/image.1.png]]
* upon several more forwards, we see the login credentials along with **a token** 
		
	* {"email":"[wiener@hotdog.com](mailto:wiener@hotdog.com)",
	* "username":"wiener",
	* "token":"9CrWvb5XTmMQfpme6OHySTIoaP6\_65bE1ZxQxQCKHCP"}

1.  
	* \- now that we know the AuthO token, we can log in as another user with knowing just their email address
	* \- we need to use the HTTP History and the Repeater in Burp; we send POST request with the above credentials to the repeater, but now we change the email address to that of Carlos, then send the request
	* \- we can right-click the POST request and select “Request in browser” → “In original session”
	* \- we copy the URL in the resulting window, then past it into the a browser
	* \- we are now logged in as Carlos
