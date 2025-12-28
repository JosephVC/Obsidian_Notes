---
source: https://academy.hackthebox.eu/module
---
HTTP stands for HyperText Transfer Protocol; hypertext is text containing links to other resources

communication via HTTP consists of a client and server, where the client requests resources from the server.  the server process the request and provides the appropriate resource.  the default port for HTTP is 80, but this can be change.  to use the internet as we are accustomed to, we enter a **Fully Qualified Domain Name (FQDN)** as a **Uniform Resource Locator (URL)** in order to reach the desired website

**The structure of a URL**

![url_structure.png](https://academy.hackthebox.eu/storage/modules/35/url_structure.png)

* **Scheme**
	* used to identify the protocol used to identify the client; usually http or https
* **User**
	* optional component that contains credentials in the form of **username:password** in order to authenticate to the host
* **Host**
	* signifies the resource location. this can be a hostname or an IP address; a colon separates a host and a port
* **Port**
	* if there is not a port number specified, the URL points to the default port of 80; if HTTP isn't running on port 80, it can be specified in the URL
* **Path**
	* this points the resource being requested; if no path is specified the server returns the default index document, such as index.html
* **Query String**
	* preceded by a question mark; an optional component that is used to pass information to the requested resource; 
	* a query string consists of a parameter and a value; you can use a **&** to separate multiple parameters
* **Fragment**
	* processed by the browsers on the client-side to locate specific resources within the main resource, such as particular headings within a web page

**HTTP Flow**

![HTTP_Flow.png](https://academy.hackthebox.eu/storage/modules/35/HTTP_Flow.png)

**HTTPS Overview**

* a drawback of HTTP is that all data is transferred in clear text, meaning anyone can perform a MITM attack to see the transferred data
* tools like wireshark can be used to sniff traffic:
	* ![https_clear_convo.png](https://academy.hackthebox.eu/storage/modules/35/https_clear_convo.png)
* **the default port for HTTPS is 443, which is preferred over port 80**

**HTTPS Flow**

**![HTTPS_Flow.png](https://academy.hackthebox.eu/storage/modules/35/HTTPS_Flow.png)**

* it may be possible for an attacker to perform an **HTTPS downgrade attack**, which downgrades HTTPS traffic to HTTP
	* this sort of downgrade attack is done via MITM attack and passing traffic through an attacker-controlled proxy

**HTTP Headers**

HTTP headers provide a way to pass information between client and server

1. **General Headers**

* these don't respond specifically to a request or a response but rather are contextual and used to describe a message rather than its contents
	* Date - holds the date and time the message originated
	* Connection - dictates whether the network connection should stay alive after the request finishes
		* close - this value, from either the server or the client, means terminating the connection
		* keep-alive - indicates the connection should be kept open

2. **entity headers**

* entity headers can be common to both request and response
* used to describe  the content (entity) being transferred by a message
* usually found in responses as well as POST, PUT requests
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.png]]
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.1.png]]

3. **Request Headers**

* the client sends request headers in the HTTP transaction (defined in RFC 2616)
* used in an HTTP request  and do not relate to the content of the message
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.3.png]]
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.2.png]]

4. **Response Header**

* can be used in the HTTP response and don't relate to the message's content
* RFC 7231 contains more info on response headers
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.5.png]]
* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.4.png]]

5. **Security Headers**

* given the variety of web-based and browser-based attacks, it was necessary to define certain headers that enhanced security
* **security headers** are a class of response headers used to specify certain rules and politices followed by the browser while accessing the website    

            **![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.7.png]]**

            **![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.6.png]]**

**HTTP Methods and Codes**

when accessing resources, multiple HTTP methods can be used.  Among other things, these methods are meant to tell a server how to process a request and how to send back a reply

![[./_resources/Hack_the_Box_-_Web_Requests.resources/unknown_filename.8.png]]

**Response Codes**

a server will use HTTP status codes to tell a client whether the request was successful; five status codes can be returned:

* **1xx** - provides information and continues to process the request
* **2xx** - positive response codes when a request succeeds
	* **200 OK** is returned when there has been a successful request and the response generally contains the requested resource
* **3xx** - returned when the server redirects the client
	* **302 Found** - redirects to another URL, such as to a website's dashboard after a successful login
* **4xx** - improper request from a client, such as requesting a resource that does not exist or requesting a bad format
	* **400 Bad Request** - usually returned when encountering a malformed request, such as when the request has a missing line terminator
	* **403 Forbidden** - the client does not have appropriate access to the requested resource; or when the server detects malicious input from a user
	* **404 Not Found** - when a requested resource does not exist on the server
* **5xx** - returned when there is some problem with the HTTP server itself
	* 500 Internal Server Error - returned when the server cannot process the request

**GET Method**

* the GET method is the most commonly used method
* its main purpose is to request a given resource and retrieve it
* using query parameters, you can send data through a GET request
	* depending on the amt of data needing to be sent through, you'll need a POST request to send more data

**POST Method**
compared to the GET method, POST takes user parameters and places them in the HTTP request body.  This has three main benefits

* **Lack of Logging**
	* POST can handle tasks such as file uploads and user logins
	* logging the above can result in a local disk filling with sensitive information
		* thus, when we see a form accepting GET requests, we should flag it as it may result in credentials being stored in  log files
* **Less Encoding Requirements**
	* URLs need to conform to characters that can be converted to letters
	* a POST request places data in the body which can accept binary data, and the only characters that need to be encoded are those that are used to separate parameters
* **More data can be sent**
	* max URL length depends on browsers, web servers, content delivery networks, or URL shorteners
	* URLs should be kept below 2000 characters

**Examining the Request**

* by clearing cookies, you never notify the web server that you want to log out, and it will not have a chance to terminate your cookies
* if your cookies are intercepted, whoever intercepts them would have access to your account until they expire (approx. 30 days)

**Session cookies**

* you can tell if a session cookie is a hash, which you can identify as hashes
	* contain only hex characters (a-f, 0-9)
	* are divisible by 8
* ever user of a web app has a session ID, mapping to a file or location in a database, which stores information about your login
* MORE ..  .

**Content-Type**

the content-type header is crucial to a POST request as it tells the server what type of content to expect

**Getting to an Admin page while logging in as a Guest**

* go to a given target, in this case **206.189.20.127:30901**
* open up Burp Suite and its browser within the Proxy section
* copy the target URL into the browser and user Burp to forward requests until you come to a login screen
* enter **guest** as both the username and password, using Burp **forwarding only once** to intercept the request and **see the cookie information**
	* if you forward the login request more than once, you'll lose the cookie information we're looking for
	* ![[./_resources/Hack_the_Box_-_Web_Requests.resources/burp suite proxy info.png]]
* now that we have access to the login cookie, we can simply delete the information that is after **"auth"** and replace it with **admin**
* now that the cookie sees us as an admin, we should now have access to the admin site despite initially logging in as a guest

**PUT and DELETE Methods**

**cURL**

* curl is a command-line utility which supports HTTP in addition to other protocols, making it good to use in scripts and automation in general
* curl does not render HTML or run JS, so the page contents are provided to use raw
* curl understands the standard URL format, which allows us to specify credentials in the URL
	* **curl <http://admin>:[password@inlanefreight.com](mailto:password@inlanefreight.com)/ -vvv**
	* **curl -u admin:password  <http://inlanefreight.com/> -vvv**
* curl does not cache credentials like browsers, so we'll have to specify them per each request we make
	* **curl -u admin:password '<http://inlanefreight.com/search.php?port_code=us>'**
* the **\-d** flag can be set to pass **application/x-www-form-urlencoded** data 
	*  **curl -d 'username=admin&password=password' -L <http://inlanefreight.com/login.php>**
	* when the **\-d** flag is set, curl send a POST request
* **cookie usage** can be specified with the **\--cookie** or **\--cookie-jar** flag
* you can specify which HTTP method you want to use with the **\-B**
