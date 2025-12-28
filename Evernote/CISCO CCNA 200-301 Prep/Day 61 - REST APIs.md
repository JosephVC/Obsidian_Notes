---
---
**APIs**

* an API is a software interface that allows two applications to communicate with each other
* APIs are essential not just for network automation, but for a variety of applications
* in SDN architecture, APIs are used to communicate between apps and the SDN (via the NBI), and between the SDN controller and the network devices (via the SBI)
* The NBI typically uses REST APIs
* NETCONF and RESTCONF are popular southbound APIs

**CRUD**

* CRUD (Create, Read, Update, Delete) refers to the operations we perform using REST APIs
* **Create** operations are used to retrieve the value of a variable
	* what is the value of the variable "ip\_address"?
* **Read** operations are used to retrieve the value of a variable
* **Update** operations are used to change the value of a variable
* **Delete** operations delete variables
* HTTP uses **verbs (aka methods)** that map to these CRUD operations
	* example: using the GET verb to get data from a server
* REST APIs use HTTP for their application-layer protocol

**HTTP Verb**

![[./_resources/Day_61_-_REST_APIs.resources/unknown_filename.1.png]]

**HTTP Request**

* when an HTTP client sends a request to an HTTP server, the HTTP header includes information like this:
	* an HTTP verb (ie. GET)
	* a **URI (Uniform Resource Identifier)**, indicating the resource the client is trying to access
	* ![[./_resources/Day_61_-_REST_APIs.resources/unknown_filename.png]]
	* Here's an example of a URI 
		* ![[./_resources/Day_61_-_REST_APIs.resources/unknown_filename.3.png]]
* the HTTP request can include additional headers which pass additional information to the server
	* ![[./_resources/Day_61_-_REST_APIs.resources/unknown_filename.2.png]]
* an example would be an **Accept** header, which informs the server bout the type(s) of data that can be sent back to the client
	* ie: **Accept: application/json** or **Accept: application/xml**
* you can also view standard HTTP header fields with some examples at **wikipedia: list of HTTP header fields**
* **When a REST client makes an API call (request) to a REST server, it will send an HTTP request like the one above; you need to know some things about HTTP to understand how REST works**
	* REST APIs don't **need** to use HTTP for communication, although HTTP is the most common choice
	* for the CCNA, assume HTTP is being used

**HTTP Response**

* the server's response will include a status code indicating whether the request succeeded or failed, as well as other details
* the first digit indicates the class of the response:
	* **1xx** **informational:** the request was received, continuing process
		* **102 Processing:** indicates that the server has received the request and is processing is not yet available
	* **2xx successful:** the request was successfully received, understood, and accepted
		* **200 OK:** indicates that the request succeeded
		* **201 Created:** indicates that the request was successful and a new resource was created (such as in response to POST)
	* **3xx redirection:** further action needs to be taken in order to complete the request
		* **301 Moved Permanently:** indicates that the requested resource has been moved, and the server indicates its new location
	* **4xx client error:** the request contains bad syntax and can't be fulfilled
		* **403 unauthorized:** means the client must authenticate and get a response
		* **404 Not Found:** means the requested resource is not found
		* ![[./_resources/Day_61_-_REST_APIs.resources/image.png]]
	* **500 Internal Server Error:** means the server encountered something unexpected that it doesn't know how to handle

**REST**

* **Representational State Transfer**
* **REST APIs are known as REST-based APIs or RESTful APIs**
	* REST isn't a specific API, but rather describes a set of rules about how the APIs should work
* **The 6 constrains of RESTful architecture**
	* **uniform interface**
	* **client-server**
		* REST APIs use a client-server
		* the client uses API calls (HTTP Request) to access the resources on the server
		* the separation of both client and server means that both can evolve independently of each other
			* when the client application changes or the server application changes, the interface between them must not break
	* **stateless**
		* REST APIs are stateless
		* this means that each API event is a separate event, independent of all past exchanges between the client and server
			* the server does not store information about previous requests from the client to determine how it should respond to new requests
		* if authentication is required, this means that the client must authenticate with the server for each request it makes
		* TCP is an example of a stateful protocol
		* UDP is a stateless protocol
		* while REST APIs use HTTP, which uses TCP (stateful) as its L4 protocol, HTTP and REST APIs aren't stateful.  The functions of each layer are separate
	* **cacheable or non-cacheable**
		* REST APIs must support caching of data - keeping data for future use
			* this improves performance of the client and reduces loads on the server
			* not all resources have to be cacheable, but cacheable resources MUST be declared as cacheable
	* **layer system**
	* **code on demand**
	* <https://restfulapi.net/rest-architectural-constraints/>
	* for applications to communicate over a network, networking protocols must be used to facilitate those communications
		* for REST APIs, HTTP(S) is the most common choice
	* **for the CCNA, make sure you know the CRUD actions, HTTP client request verbs, HTTP server response codes, and the basic characteristics of REST APIs**

Cisco DevNet

* DevNet is Cisco's developer program to help developers and IT professionals who want to write applications and develop integrations with Cisco products, platforms, and APIs
* DevNet offers free resources to learn about automation and develop skills

**QUIZ**

1. ![[./_resources/Day_61_-_REST_APIs.resources/image.1.png]]

* B

2. ![[./_resources/Day_61_-_REST_APIs.resources/image.2.png]]

* c

3. ![[./_resources/Day_61_-_REST_APIs.resources/image.3.png]]

* b

4. ![[./_resources/Day_61_-_REST_APIs.resources/image.4.png]]

* c

5. ![[./_resources/Day_61_-_REST_APIs.resources/image.5.png]]

* a

6. ![[./_resources/Day_61_-_REST_APIs.resources/image.6.png]]

* A, B
* ![[./_resources/Day_61_-_REST_APIs.resources/image.7.png]]
