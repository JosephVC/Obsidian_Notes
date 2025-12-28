---
---
    HTTP based mechanism that checks the origin of what resources a browser loads.  the origin could be a domain, scheme, or port.  CORS also uses a **preflight request** containing the the HTTP method and headers that will be in the actual request to the server hosting the cross-origin resource to see if the server will permit the actual request.  Requests that are considered "simple" don't trigger the need for a preflight request, but types of requests need to meet all of a variety of requests.  

For security reasons, browsers restrict cross-origin HTTPrequests initiated from scripts, such as using the **same origin policy**.  this means that [domain-a.com](http://domain-a.com) can only request resources from [domain-a.com](http://domain-a.com) without running  into trouble with CORS

![[./_resources/CORS.resources/cors_principle.png]]
