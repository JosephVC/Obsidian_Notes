---
---
**RESTful Web API Notes**

the representation of resource is when a source sends a a document in response to a query

* the URL identifies the resource

response/status codes are simply ways for someone to tell what happened to a client request

an HTTP session lasts for one request

* this principle is called **statelessness**, as the server does not know the user exists, or what state the user is in, and only responds to requests 

the resource represented in the browser is the **application state** 

the **resource state** is the state of resources served

**connectedness**: each web page tells you how to get to the adjoining page; the web exists based on this connectedness

**HATEOAS**: Hypermedia As The Engine Of Application State

* links and forms determine how servers provide resources 

Semantic challenge: the technical structure of a web page vs what the content means for humans

3 basic parts of an HTTP response:

* status code: summary of the status of the response (fail, succeed, etc.)
* as the GET request is a request for representation, the entity body is what is represented 
* response headers: key/value pairs describing the entity body and HTTP response
	* content type: tells HTTP client how to understand the entity body; equivalent to media type/MIME type

Collection + JSON: standard for publishing searchable lists

REST is a set of design constraints

* statelessness, HATEOAS, etc.
* Fielding Constraints

REST is an example of **tying the web to a design concept**; it describes the architecture of the web

**3 essential web technologies**: URL, HTTP, HTML

* resources and representation underlie the 3 above

a POST, PUT, PATCH is a client sending a representation of a resource; the server tries or **refuses to** create that resource

* this **sending of a representation** of a state the client wants is representational state transfer

in a RESTful system, clients and servers interact only by sending messages following a predefined protocol

PATCH, PUT: modify part of a resource

* these are protocol semantics

DELETE: is **indempotent**; the resource state has permanently changed and sending a new request will not get any new result

* if there are network hiccups, sending multiple requests will not cause undue change

PATCH is neither safe nor indempotent

* if you apply the same PATCH to the same document, you'll get an error the next time

POST is effectively any type of change - PUT, DELETE, PATCH, LINK, UNLINK - all rolled into one

* an HTML form cannot trigger a PUT request, so it uses POST (due to HTML data format)

it is legal to send any data as part of a POST request; POST does not necessarily mean "create a new resource" but "do whaterver"

* the latter is an **overloaded POST** 
	* this can only be understood in terms of application semantics

standard HTML tags describe four kinds of HTTP requests

* <a> describes GET for one URL, and only if the user triggers the command
* <img> describes GET for one URL, automatically
* <form> + a method = POST
	* describes POST to one URL, with a body described by the client, if latter triggers the control
* <form> + a method = GET
	* describes GET request for custom URL constructed by the client, only if user triggers the control

all the HTML documents we read fall under the **presentation of information**

URL: a short string used to identify a resource; same for a URI ('i' at the end rather than an 'L')

* every URL is a URI
	* noted in the standard RFC 3986
* there is no guarantee a URI has a representation
	* a URI does nothing but identify a resource
* a URL can be **dereferenced** the computer can take a URL and represent its underlying resource
* an ISBN is a good example of a URI; it identifies a resource but o=does not provide a representation
* URI's on an FTP can both identify and provide a representation\\

Without a URL, there can be no representation, thus no representational state transfer

a resource identified by a URL can fulfill all the Fielding Constraints

* uniform interface: HATEOAS
* client-server setup
* stateless: each session is treated as new
* cachable: improves performance + reliability
* layered systems: ability to use layered system architecture 

What is hypermedia for?

* tell client how to construct HTTP request; the HTTP method to use; the URL to use; what HTTP header and/or entity body to send
* promise certain static code response, date sent in response
* suggest how the client should integrate response into workflow

4 parts of an HTTP request

* method (GET, PUT POST, ect.)
* target URL
* HTTP headers
* entity body

embedded links don't replace the clients application state; they augment it

**transclusion**: embedding one document in another

* items in <script> tags are not transcluded 
* various tags give the browser **hints** as to the proper requests for the client

hypermedia controls can bridge the semantic gap, in telling a client why it might want to make a certain HTTP request

**link relation** - helps bridge semantic gap; define relations ('up', 'down') and program these relations into an API

* explains the change in application state (for safe requests) or resource state (for unsafe requests) that happen when the client triggers a control

**well-made API:** API where anyone can use or write a client, or even a server

* anyone using the API becomes partner in its implementation, thus changing the API becomes difficult without disrupting service

hypermedia designs are more flexible as they are based on the basic design of the web

**monitor:** simulates a human monitoring one page, rather than a crawler that looks at a lot of pages

* like an RSS aggregator 

a **collection**  is a special type of response (anything important enough to warrant its own URL) that lists the resources by linking to them

* item/member/entry: individual resources in a collection 

the collection pattern recognizes three different types of resources

* item: type resources responding to GET, PUT, DELETE
* collection-type resources (GET, POST)
	* collection types **contain** item-type resources
* when the collection type links to these items, it includes a partial representation of them

the distinction between collection and an item is a layer of application semantics on  top of HTTP's protocol semantics

an item in a collection doesn't mean anything, though (???)

even if everyone used collection + JSON for their API, we'd still have multiple definitions of what an 'item' means
