---
---
**Deploying Django app to Heroku**

<https://devcenter.heroku.com/articles/getting-started-with-python?singlepage=true>

the **Procfile** using **gunicorn** needs to have a structure like **web: gunicorn \[name of whatever directory has your settings.py file in it\].wsgi --log-file -** 

there is also Windows-specific **Procfile** that look like **web: python manage.py runserver 0.0.0.0:5000**

**If you get an "app not compatible" error** when pushing to heroku, then try resetting the heroku/python buildpack with **heroku buildpacks:set heroku/python**

You don't need to have your github repo be the same name as your django/heroku app

to create a **requirements.txt** file from poetry:  **poetry export -f requirements.txt > requirements.txt**

* the above will produce a requirements.txt file that is very voluminous compared to what you might find in other projects: 

                        ![[./_resources/Untitled_Note.resources/unknown_filename.png]]

* this isn't necessarily bad, though

 run migrations on your django app within the heroku cli with **heroku run python manage.py migrate**

**I had to run migrations before things deployed and worked properly**

* If you don't have a database environment variable already set when starting out, you probably didn't deploy correctly
