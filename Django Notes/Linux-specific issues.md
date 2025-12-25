---
---
When trying to start the backend on Ubuntu 20.04, I received the following error :

**ModuleNotFoundError: No module named 'django\_heroku'**

google search led me to a [post](https://stackoverflow.com/questions/57416061/django-heroku-modulenotfounderror-no-module-named-django-heroku) saying the reason behind this was that **psycopg2** may not be installed

 that  **django** **psycopg2** was not properly installed:

![[./_resources/Linux-specific_issues.resources/unknown_filename.png]]

**Solution**

One solution was to run 

1. **sudo apt-get install python3-pip**
2. **pip3 install psycopg2-binary**
3. **sudo apt-get install libpq-dev**
4. **pip3 install psycopg2**
5. **poetry add psycopg2**
