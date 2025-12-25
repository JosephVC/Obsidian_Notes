---
---
**Django apps** 

when you run django-admin startapp \[whatever-app-name\], you need to do it where the app is visible to manage.py, otherwise **settings.py** won't see the app and there will be problems when a **manage.py** process is run

Look at the below project structure to see **what  not to do**

![[./_resources/Untitled_Note.9.resources/unknown_filename.png]]

See where the **post** application is inside the **backend** directory, where **manage.py** cannot see **posts,** so even when the app is correctly added to **settings.py** things don't work

![[./_resources/Untitled_Note.9.resources/unknown_filename.1.png]]

the above structure, where the **post** application is nested within the **backend** directory, which contains **manage.py**.  This allows the latter application to see whatever other apps we  make within **backend**
