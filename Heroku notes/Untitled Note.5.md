---
source: https://app.slack.com/client/T03LJKBP8/D9LDFFSKC
---
**Setting up OCR project using Tesseract** 

You'll need an **Aptfile** with the following:

* tesseract-ocr
* tesseract-ocr-eng
* libpng-dev
* libtesseract-dev

**The Procfile:**

web: gunicorn \[name of your parent directory\].wsgi --log-file -

**Buildpacks:**

\=== django-ocr-backend Buildpack URLs
1\. heroku/python
2\. <https://github.com/heroku/heroku-buildpack-apt>
3\. <https://github.com/pathwaysmedical/heroku-buildpack-tesseract>
