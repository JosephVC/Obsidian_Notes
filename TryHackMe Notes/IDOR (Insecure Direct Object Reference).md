---
---
**What is an IDOR**

* type of access control vulnerability
* where too much trust has been placed on the input data, and the receiving server does not perform proper validation on the input to ensure the requested object belongs to the user requesting it
* **for example**, if you go to a website - <http://online-service.thm/profile?user_id=1305> - and you change the given user ID to see another user's information

**Encoded IDs**

* raw data on web pages is often encoded  to ensure servers are able to understand the contents
	* base64 encoding is one of the most common encoding formats
* there are site to decode, change, and then re-encode data to tamper with sites
	* <https://www.base64decode.org/>
	* <https://www.base64encode.org/>
	* ![[./_resources/IDOR_(Insecure_Direct_Object_Reference).resources/image.png]]
* ID's can be **hashed**, rendering them to a long random string of characters
	* these hashes can be decoded at sites like <https://crackstation.net/>

**Unpredictable IDs**

* you can create two accounts on a site  to see how they handle IDs, swapping the IDs between accounts while still logged in to see whether you can see the other account's info

**Vulnerability Location**

* IDOR vulns can be located in a variety of places other than the address bar
	* JS files loaded
	* AJAX requests
