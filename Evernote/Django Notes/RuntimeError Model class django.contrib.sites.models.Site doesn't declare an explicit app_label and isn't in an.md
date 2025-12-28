---
---
if you are trying to install django-allauth into a project and get the following error:
![[./_resources/RuntimeError_Model_class_django.contrib.sites.models.Site_doesn't_declare_an_explicit_app_label_and_isn't_in_an.resources/unknown_filename.png]]

it's likely because you forgot to add **'django.contrib.sites'** your your **INSTALLED\_APPS** list above where you note the 'allauth' app name:

![[./_resources/RuntimeError_Model_class_django.contrib.sites.models.Site_doesn't_declare_an_explicit_app_label_and_isn't_in_an.resources/unknown_filename.1.png]]
