---
---
Ever since install **django-admin-honeypot**, I've had my DEBUG var set to  False and I've been getting a 500 error whenever I try and access either the honeypot admin site or the re-named genuine admin site.

**SOLUTION**

**Logging** was installed in settings.py which allowed me to see that the problem was:

**ValueError: Missing staticfiles manifest entry for 'admin/css/base.css**

This was ultimately caused by some static files not being recognized.  There was an additional static files directory noted in my AWS settings:

STATICFILES\_DIRS = \[
    os.path.join(BASE\_DIR, 'mysite/static'),
\]

 and this was deleted.  Then **python manage.py collectstatic** was run, and this solved the issue.
