---
---
**based on:** **<https://auth0.com/docs/authorization/which-oauth-2-0-flow-should-i-use#oauth-2-0-terminology>**

**Basic Terminology**

* **Resource Owner:** entity that can grant access to a protected resource, typically the end user
* **Client:** the application requesting access to a protected resource on behalf of the Resource Owner
* **Resource Server:** server hosting the protected resources; the API you want to access
* **Authorization Server**: the server that authenticates the Resource Owner and issues access tokens after getting proper authorization
* **User Agent:** agent used by the Resource Owner to interact with the client; examples would be a browser or native applications 

**Flow**
There are different flows (grants) that are supported by the OAuth Framework.  The right one depends on one's application type and other factors.  

* **is the Client the Resource Owner?**
	* is the party that requires access to the resource a machine?  when it comes to machine-to-machine authorization, there is no end-user authorization needed as the Client is also the Resource Owner.
		* an example is a cron job that uses an API to import information to a database; here the cron job is both the Client and Resource Owner since it holds both the client ID and client secret and gets the access token from the authorization server
	* if so, use the Client Credentials Flow
* **Is the Client a web app executing on the server**
	* If the Client is a web app executing on a server then the **Authorization Code Flow** is applicable.  Here the Client retrieves the Access token and, optionally, a Refresh Token .  this is considered safe as the access token is passed directly to  the web server hosting the Client but without going through the user's web browser and the potential risk of exposure
* **Is the Client absolutely trusted with user credentials?**
	* here the end user is required to fill in credentials into a form
	* the above info is sent to Auth0, thus the client must be completely trusted with this sort of information.
	* The flow necessary for this is **Resource Owner Password Credentials Grant,** but only when redirect-based flows are not possible
* **Is the Client a Single-page App?**
	* if the client is a sort of single-page app running in the browser via something like JavaScript, you can either use the **Authorization Code Flow with Proof Keys for Code Exchange (PKCE)** and the **Implicit Flow with Form Post**.  Auth0 prefers using the former as the access token is not exposed on the client side, and the flow can return refresh tokens
	* if the SPA does not need an access token, use the **Implicit Flow with Form Post**
* **Is the Client a Native/Mobile App?**
	* If the app is native, use **Authorization Code Flow with Proof Keys for Code Exchange (PKCE)**
*
