---
---
a web application or even simple web page works by passing information over the Net.  this information is often passed as an object.  these objects are comprised of various files or properties.  Objects can contain files as attachments.  Request/response objects are sent over the web. HTML, CSS, JS, etc. are all **Response Objects.**  

**HTTP**

* interchanges between servers and client machines follow rules, on set of rules being **HyperText Transfer Protocol (HTTP).**  The **Request Objects** contain the request made by the client.  the server with the relevant information will respond according to the information in the Request Object.  **The information served by the server to the client is the Response Object.**
* **![[./_resources/Django_RequestResponse_Cycle.resources/unknown_filename.1.png]]**
* **Request**
	* requests are smaller in size than responses, as the response needs to carry back the contents of a web page, etc.
	* a request is a **request made by the client to the server**
	* any URL that gets searched is a request
	* request objects give information to the server; forms filled and images uploaded are transferred as **attributes of the Request object**
	* the server then accesses this information and calls its own functions
* **Response**
	* the response is heavier (in bandwidth) than the request, as it usually contains HTML, CSS, JS, images, etc. 
	* **Header contents of a response:**
		*  **![[./_resources/Django_RequestResponse_Cycle.resources/unknown_filename.png]]**
			* **Date, server information, the type of content sent, etc. are sent within the Header**
		* the header of a response will contain what amounts to the metadata of the response

**Django Request-Response Cycle**

1. django can be considered as an application on the server whose main task is to process the request received by the server
	1. in processing the request received, it then calls functions to provide a response
2. when a request comes into django, it is processed by the **middleware**
	1. when django first starts up the server it loads the middleware after settings.py
3. the request is then processed by various middlewares one by one; the response is processed differently by different types of middleware (some middleware checks security, etc.).  for instance, if the request does not meet the security standards of the middleware it is not allowed to proceed further
4. Once the request is processed through the middleware, it passed to the **URL Router**
	1. the router simply extracts  the URL from the request and will try to match it to defined urls (in your **urls.py** file)
5. Once we get the matching URL the view function linked to that URL is called
	1. this function will get various attributes and other URL parameters
	2. the view function will will be able to access files from the requests
6. these requests are considered to be **HttpRequest class objects** 
	1. the requests module is a **python module** that provides various methods for Request objects
7. once the view function has been executed, now we get a response
	1. the response is given in the form of **HttpResponse** 
	2. the response can be PDF, JSON, CSV; django provides built-in support to provide responses of various types
8. when the response is rendered it will look for HTML, which will be processed by the **Django Templating Engine**
	1. once that completes django simply sends the files as any server would and the response will contain the HTML and other static files
