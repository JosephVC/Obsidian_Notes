---
source: https://devcenter.heroku.com/articles/getting-started-with-python?singlepage=true
---
**Locally running your app**

1. Make sure you have all your requirements installed with **pip install -r requirements.txt**
2. Assuming you're using **Django**: **python manage.py collectstatic**
3. **\*If on Windows\* -** use the Windows-specific Procfile: **heroku local web -f Procfile.windows**
4. the local web server will start up, and you can go to localhost:5000 to see the site
