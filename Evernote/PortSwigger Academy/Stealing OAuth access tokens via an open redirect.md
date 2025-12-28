---
---
* this lab uses an OAuth service to allow users to log in with a social media account
* a flawed validation by OAuth makes it possible for an attacker to leak access tokens
* we need to identify an open redirect on the blog website and use  this to steal an access token for the admin user's account
* this access token will be used to obtain the admin's API key and then submit the solution using the button provided in the lab banner

* from logging in with a real account - peter:wiener, we see via the proxy the following:
	* ![[./_resources/Stealing_OAuth_access_tokens_via_an_open_redirect.resources/image.png]]
* after several forwards, we receive the following credentials
	* [{"email":"wiener@hotdog.com](mailto:{"email":"wiener@hotdog.com)","username":"wiener","token":"1rrhtFews5\_aeTLtzdmuhrICW5bxZxiCrgOx-7M16j8"}
* **don't forget to look in the HTTP history**
	* we see from this history an odd GET request to a "/me" endpoint
	* we send the above request to the repeater
