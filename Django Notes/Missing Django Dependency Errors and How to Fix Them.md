---
source: https://app.slack.com/client/T03LJKBP8/D9LDFFSKC
---
**Missing Dependency Errors and How to Fix Them**

![[./_resources/Untitled_Note.4.resources/unknown_filename.png]]

this error was fixed by altering the Aptfile in the main directory, adding libpng-dev and libtesseract-dev

After this error is fixed, another pops up:
![[./_resources/Untitled_Note.4.resources/unknown_filename.1.png]]

this is Heroku not finding a right thing in the database; you solve this with **heroku run python manage.py migrate**
