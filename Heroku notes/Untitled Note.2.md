---
---
**The 'Module Not Found" error in Heroku logs**

![[./_resources/Untitled_Note.2.resources/unknown_filename.png]]

this likely popped up due to me renaming the top directory of the project to the above name from "mysite" where every other directory and file in the project referred to "mysite"  

The Profile initially referred to the new name, but altering the Procfile to read **web: gunicorn mysite.wsgi --log-file -** seemed to fix the problem
