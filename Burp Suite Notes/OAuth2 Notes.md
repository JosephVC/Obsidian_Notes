---
source: https://portswigger.net/web-security/oauth/grant-types
---
**OAuth Grant Types**

* OAuth grant types determine the sequence of steps that are needed in the OAuth process
* Grant types are referred to as **OAuth flows**
* for any grant type, an application has to specify what data it wants and the type of authorization it wants to perform; this is done using the **scope** parameter
	* the scopes to request access are particular to each OAuth service; as the scope is just a string, the format can vary between providers
		* scope=contacts
		* scope=contacts.read
		* scope=contact-list-r
		* scope=<https://oauth-authorization-server.com/auth/scopes/user/contacts.readonly>
	* when used for **authentication** the standard OpenID Connect scopes are often used

**Authorization Code Grant Types**

* the client application and OAuth service first uses redirects to exchange  a series of browser-based HTTP requests that initiate the flow
* if a user consents to a request for access, and if they do an **authorization code** is created
* the client then exchanges this code with the OAuth service to receive **access token** which they can use to make API calls to fetch the relevant user data
* the above code/token exchange is done beyond the sight of the user,  using a custom secure back-channel established when the client application first registers with the OAuth service
* when the client application registers with the OAuth service, a **client\_secret** is generated, which is necessary for the client application to authenticate itself when sending server-to-server requests
* the most sensitive data (access token and user data) is not sent via the browser; making this form of grant type the most secure; server side applications should always use this sort of grant type
* ![[./_resources/OAuth2_Notes.resources/unknown_filename.png]]

1. **Authorization Request**

* ​the **/authorization** endpoint receives the client application's request for permission to particular user data
* the request will likely have the following parameters 
	* **client\_id**
	* **redirect\_url**
	* **response\_type**
	* **scope**
	* **state**

2. **User Login and Consent**

* when the authorization server receives the initial request it'll send the user a login page; the user will be prompted to log in to their account with the OAuth provider
* the user will then be presented with data the client wants to access (defined by scopes set in the authorization request); the user can consent or not to this access
* as long as the user has a valid session with the OAuth service, the above steps will be completed automatically
	* so, the first time a user logs in to a social media service they will have to manually complete steps to do so, but from then on they can log in with a single click

3. **Authorization Code Grant**
	

1. **Access Token Request**
2. **Access Code Grant**
3. **API Calls**
4. **Resource Grant**

**Implicit Grant Type**

* **​**​rather than obtain an authorization code and then exchanging it for an access token, the client application receives the access token immediately after the user gives consent
* this type is far less secure, as there is no secure back channel to send data but only browser redirects; the user's data is more vulnerable to attack this way
* this grant type is better suited to single-page applications and native desktop applications, as these programs can't store the **client\_secret** on the back end and thus don't really benefit from using the authorization code type
* ![[./_resources/OAuth2_Notes.resources/unknown_filename.1.png]]
