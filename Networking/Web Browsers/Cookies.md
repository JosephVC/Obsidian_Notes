---
---
https://www.microsoft.com/en-us/edge/learning-center/what-are-cookies?form=MA13I2

https://www.cloudflare.com/learning/privacy/what-are-cookies/

https://whatismylocation.org/blog/browser-fingerprinting-explained


You've probably heard of cookies before, they're just a small  piece of data that is stored on your computer. Cookies are saved when  you receive a "Set-Cookie" header from a web server. Then every further  request you make, you'll send the cookie data back to the web server.  Because HTTP  is stateless (doesn't keep track of your previous requests), cookies  can be used to remind the web server who you are, some personal settings  for the website or whether you've been to the website before. Let's  take a look at this as an example HTTP request:

![[cookie_flow.png]]
Cookies  can be used for many purposes but are most commonly used for website  authentication. The cookie value won't usually be a clear-text string  where you can see the password, but a token (unique secret code that  isn't easily humanly guessable).

**Viewing Your Cookies**
You  can easily view what cookies your browser is sending to a website by  using the developer tools, in your browser. If you're not sure how to  get to the developer tools in your browser, click on the "View Site"  button at the top of this task for a how-to guide.
Once  you have developer tools open, click on the "Network" tab. This tab  will show you a list of all the resources your browser has requested.  You can click on each one to receive a detailed breakdown of the request  and response. If your browser sent a cookie, you will see these on the  "Cookies" tab of the request.


- Session cookies
	- tracks a user's session and are usually removed when a user exits a website or logs out
	
- persistent cookies
		- these contain an expiration date and will remain on a user's system for a set length of time
		
- authentication cookies
	- helps manages user sessions by associating correct user acct. information with a cookie identifier string
	- ensures the correct information is delivered to the correct user 

- tracking cookie
	- used by tracking services
	- a record of browsing activity is sent to a given organization the next time a user visits a site using that tracking service

- zombie cookies
	- stored outside the normal place cookies are saved on a system

- third party cookie
	- belongs to a domain other than what is displayed in the browser