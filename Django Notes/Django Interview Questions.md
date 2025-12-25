---

tags: 
  - Interview

---
If you don't understand something and look it up later, round back with the interviewer to let them know.  It at least shows you give a shit about learning

* What is your dream project?
	* Right now it would be a django equivalent of the OWASP Juice Shop, an app that would teach people about web app security via an app that is itself deliberately insecure and which would guide people through the steps of securing it
* what's the difference between django and flask?
	* django is more complex than flask, coming with more features built into it but also capable of being more scalable and able to create more complicated websites
		* how is django more scalable
			* **vertical scaling:** more resources are used on the computers running an application
			* **scaling horizontally:** a larger quantity of machines are used to run the application
			* django can take advantage of a variety of SQL databases (and through add-ons) noSQL databases as well
			* middleware that is not useful can be removed or more useful middleware can be added

|     |     |     |
| --- | --- | --- |
| Comparison | Django | Flask |
| Project Type | supports large projects | smaller projects |
| ease of learning | more learning and practice | comparatively less |
| flexibility | allows complete development without the need for many 3rd party tools | flexible in the sense that the user can select many 3rd party tools as needed |
| visual debugging | does not support | supports |
| type of framework | batteries included | simple and lightweight; add batteries as you need them |
| bootstrapping-tool | built in | not available |

* **what is django**
	* FOSS open source python web framework
	* **why is it needed?**
		* it's not necessarily needed per se, but the fact that it comes with so much built in and is so scalable makes it very useful for a variety of cases
* **what companies use (or did use) django**
	* reddit
	* disqus
	* spotify
	* bitbucket
	* dropbox
	* mozilla
	* udemy
	* youtube
	* pinterest
	* instagram
* **What are key features in Django?**
	* great quantity of packages
	* speed of development
	* security
		* CSRF Tokens
			* cross-site scripting protection for POST/PUT/DELETE requests typically sent with forms
				* this sort of attack is when a malicous website consists of a link, some JS, or a form whose aim is to perform some action on your website by using the login credentials of a genuine user  
	* versatility
	* scalability
* **how do I check for my current version of django?**
	* "python -m django --version"
	* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.png]]

* What are the advantages of using Django?
	* loosely coupled stack - each component has little knowledge and use of the other separate components
	* capability to write less code and quick development - mainly due to using Python (right?)
	* following the DRY principle
	* SQL statements are not executed too many times **(what the fuck does this mean?)**
	* can drop into raw SQL via the Django console
	* flexibility when using URLs

* Explain the Django Architecture
	* MTV: Models/Templates/Views architecture
		* based on MVC (Model View Controller) architecture
		* in this model Django itself is the controller which sends the request to the appropriate view
			* **models** are connected to the database which is then connected to the view
			* **templates** deal with the **presentation of** the data
			* the **view** describes the **data sent to** the user
			* data from the view is then sent to the url
			* django is the controller taking the data interpreted by the view and finally presenting it to the user

* what is the **django-admin?**
	* **django-admin** is the command line utility of django used for administrative tasks
	

|     |     |
| --- | --- |
| Task | Command |
| to display usage information | django-admin help |
| list of available commands | django-admin help -command |
| See the description of a particular command | django-admin help \[command\] |
| determine the version of django | django-admin version |
| create **new** data migrations | django-admin makemigrations |
| synchronize the database state | django-admin migrate |
| start the dev server | django-admin runserver |
| send a test email | django-admin sendtestemail |
| start a python interactive interpreter within a project | django-admin shell |
| show all the migrations in a project | django-admin showmigrations |

* How do you connect django project to a database?
	* you can specify which database you want to use in **settings.py**
	* django has a default database called SQLite
		* python manage.py makemigrations
			* this will tell django there has been a change in your database models
				
		* python manage.py migrate
			* looks at the installed\_apps settings and creates the database table accordingly
			* the command is used to apply or unapply database migrations
			* synchronizes current set of models and migrations with the database state
			* can be used with or without parameters
			* all apps will have their migrations run unless another parameter is specified.
			
		* python manage.py sqlmigrate (followed by the app name and the generated ID)

* what are the sorts of boilerplate files django creates in a new project?

|     |     |
| --- | --- |
| File name | Description |
| manage.py | A command-line utility |
| \_\_init\_\_.py | an empty file that tells Python that the current directory should be considered as a Python package |
| settings.py | Setting for the current project |
| urls.py | URLs for the current project |
| wsgi.py | Entry-point for the web servers to serve the project you've created |

* what exactly are **models**?
	
	* a **model** is the single definite source of information about your data
	* a model consists of the essential fields of behavior of your app
	* each model will map to a single specific database table
	* in django, models serve as part of the abstraction layer
	* models are a subclass of **django.db.models.Model**
	* **what are model relationships**
		* **One-to-one relationships**
			*  sets a one-to-one relationship between models
		* **ManyToManyField**
			* defines a many-to-many relationships
	* **what is a ForeignKey**
		* model attribute that sets a one-to-many relationship between on model and another
	
	* **what is CharacterField**
		* basically a string value

* What are **Model Forms**
	* essentially a form generated based off of a model
		* we create a class inheriting from a form object
		* when we use the form, it autogenerates the necessary fields based on the Model it uses

* what is the **Django Rest Framework**
	* many projects either require the use of front end frameworks and/or an API
	* DRF allows to create a REST (REpresentational State Transfer) API in django which we can then connect to a front end framework like React or Angular
		* REST was defined in Roy Fielding's 2000 dissertation

* What are **serializers** and **model serializers**
	* it takes our data and serializes it into something like JSON
	* like a model form, a model serializer is based on one of our models, turning the data in that model into JSON

* **How is a request processed in Django?**
	* django first determines which root URLconf module is to be used
		* a URLconf module is your **urls.py** file
	* that particular python module is loaded
	* then django looks for the variable urlpatterns
	* urlpatterns are run by Django, which stops at the first match of the requested URL
	* then Django imports and calls the given view
	* in case none of the URLs math the requested URL, Django invokes an error-handling view

* **What is the HTTP Request/Response cycle in Django?**
	
	* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.5.png]]
	
	1. the client opens up a browser and wants to view our web page (running Django)
	2. the domain name is typed in, starting an HTTP request
	3. within this HTTP request will be the domain name we're trying to contact
	4. this request will make its way to our web server, which will handle where that data needs to go
	5. at this point, django will need to match the URL to a **view**
		1.  the view, in so far as it's connected to a database or template, will process the url
	6. the result of being processed by the view is an HTTP response

* **explain the use of middleware in django**
	* **![[./_resources/Django_Interview_Questions.resources/unknown_filename.6.png]]**
	* **you could delete the whole MIDDLEWARE section within settings.py and Django would still run, but it's not recommended**
	* middleware is a light and low-level plugin system for altering Django's input and output globally
		* the framework hooks into the **request/response** processing
		* middleware is a plugin system for globally altering Django's input and output
		* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.7.png]]
	* each component in middleware has some particular task
	* **example:**
		* in **AuthenticationMiddleware** is used to associate users with requests using sessions
	* django provides other middleware options such as **cache middleware, common middleware, GZip** middleware, etc.
	* you can simply print 'hello world' to the console, or print which view is being utilized
		* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.9.png]]
		* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.8.png]]
	* use cases?
		* allows you to filter requests
		* inject data into requests/response
		* perform logging/page analytics

* **how to query or filter the database**
	* How to query all the items in a database table
		* MyModel.objects.all()
	* How would you query a particular item
		* MyModel.objects.get(pk) 
	* How to filter by single attribute
		* MyModel.objects.filter(pk)
	* How do we filter items by multiple attributes
		
	* How to query child model objects
	* How to query upwards
		* up the chain to parent elements

* what exactly are **views?**
	* views encapsulate the logic used to process a user's request
	* either return an HttpResponse or raise an exception such as Http404
	* can read records from the database
	* can delegate to the templates, generate a pdf, etc.

* How do we set **restrictions on views**
	* How do we stop unauthenticated people from viewing certain parts of the app
		* there are built-in classes and methods that we can set either in the respective **views.py** or we can set restrictions in **settings.py**

* what exactly are **templates**?
	* renders the information to be presented to the user
	* can generate HTML dynamically
		* HTML consists of both static and dynamic data
	* you can have any number of templates
	* you can also have none of them

* What is the difference between an project and an app
	* an **app** is a web application created to do a specific task
	* a **project** is a collection of apps

* what are the **inheritance styles** in django

|     |     |
| --- | --- |
| Inheritance Style | Description |
| Abstract base classes | used when you want to use the parent class to hold information |
| multi-table inheritance | used when you have to subclass an existing model |
| proxy models | used if you only want to modify the python-level behavior of a model |

* What exactly are **static files?**
	* these are additional files such as CSS, images, or JavaScript files
	* static files are managed by **django.contrib.staticfiles**
	* these files are created within the project app directory by creating the subdirectory "**static"**  yourself
	* **What is MEDIA\_ROOT**
		* where we upload user-generated content
	* **what is 'collectstatic'**
		* collecstatic is a command we run to collect all of the static files in the project  in preparation for sending our website to production
	* **how do we serve static files in production?**
		* django itself isn't designed to server static files
			* you would need some 3rd party software like whitenoise or a cloud service like AWS

* What are **signals?**
	* what are they good for and why use them

* django consists of a signal dispatcher helping decoupled applications get notified when actions occur elsewhere in the framework
* django has a set of built-in signals that allow senders to notify receivers when a particular action is executed

|     |     |
| --- | --- |
| **Signal** | **Description** |
| django.db.models.signals.pre\_save django.db.models.signals.post\_save | Sent before or after a model's save() method is called |
| django.db.models.signals.pre\_delete<br>django.db.models.signals.post\_delete | Sent before or after a model's delete() method or queryset's delete() method is called |
| django.db.models.signals.m2m\_changed | Sent when Django starts or finishes an HTTP request |

* What is the Django **Field class**?
	* 'field' is an abstract class that represents a column in the database table
	* the Field class is a subclass of **RegisterLookupMixin**
	* in Django, these fields are used to create database tables
	* Fields are fundamental pieces in different django APIs such as models and querysets

* What are **mixins**?
	* mixins are a type of multiple inheritance which can combine the behaviors and attributes of more than one parent class
	* these are a way to reuse code from multiple classes
	* as an **example**, generic class based views consist of a mixin called **TemplateResponseMixin** whose purpose is to define the **render\_to\_response()** method
	* When this is combined with a class present in the view, the result will be a **TemplateView** class

* What are **sessions**?
	* allows you to store and retrieve arbitrary data based on **per-site-visitors**
	* this framework stores data on the server-side
	* takes care of **sending and receiving** cookies
	* these cookies consist of a session ID but not the actual data itself

* What is **context?**
	* the context in Django is a dictionary mapping template variable name given to Python objects
	* "context" is just a conventional name, and can be changed in actual code

* when can you use **iterators in the Django ORM**?
	* iterators  are containers that consist of countable number of elements
	* any object that is an iterator implements two methods - **\_\_init\_\_()** and **\_\_next\_\_()**
	* the best situation to use iterators is when you have to process results that will require a large amount of memory space
	* you can also use the **iter()** method
		* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.1.png]]

* explain some of the **caching strategies**  in Django?
	* caching means to save the output of an expensive calculation in order to prevent needlessly repeating the calculation

|     |     |
| --- | --- |
| Strategy | Description |
| Memcached | memory-based cache server |
| filesystem caching | cache values are stored as separate files |
| local-memory caching | default cache in case you have not specified any other |
| database caching | cache data will be stored in the database |

	

* what is the significance of the **manage.py** file in Django
	* this file is a command-line utility that helps you interact with your Django project
	* it does the same thing as django-admin
	* it sets the DJANGO\_SETTINGS\_MODULE environment variable

* FBV vs CBV
	* Function Based Views vs Class Based Views
	* it all depends on what you need the views to do
		* complex views may need to be in classes, while a view with one simple job could probably be a function

* what database systems do you prefer?
	* good answers are MySQL, Postgres, Oracle
		* a **noSQL** database like Mongo is not officially supported; there are 3rd party projects that allow for noSQL functionality in Django
	* **just show that you know DBs beyond SQLite**
	* **how do you set up a database**
		* in settings.py you can specify database details needed in order to connect

* What are the dynamic ways we can access URLs and why do we name URLs
	*  make sure you are not hard-coding URLs
	* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.2.png]]
	* **why name the urls?**
		* this is so  you can reference the name when making links rather than the full url in the href
		* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.3.png]]
		* the reason we do the above is that i makes the url and its path more dynamic in case we change things later on ; we're not stuck with a hard-coded url we'll have to remember to go back and change later

* Where do you store your templates
	* either in the default app structure 
		* **templates -> folder based on app name**
	* go into **settings.py** and specify exactly where you want you templates to be
	* **templating language** 
		* **jinja** and its double curly braces or curly + percent
			* these double curlies are placeholders for variables and allow us to work with data dynamically
			* the curley+percent sign are for programming logic 
				* make sure you can write a for loop or other condition statements within jinja
		*  how to include other templates
			* use the "include" keyword along with the path to the template, all within the **{% %}**

* **whitenoise** and **gunicorn**
	* **whitenoise** is a simple static file server for python web apps
	* **gunicorn** is a pure python WSGI server for UNIX
		* **WSGI** (Web Server Gateway Inteface) is a standard interface for running python web applications
	* you would use them because Django itself isn't set up to serve static files and a separate WSGI server can handle traffic loads better than django itself can

* what are the basic steps to get django into production?
	* run **collectstatic** to collect all your static files
	* make sure your secret keys are all kept in a .env file or some other way of ensuring they are not pushed into prod

* **Understand how you do authentication with just django and without the extra tools DRF gives you**

* Explain  how to use file-based sessions
	*  **file-based sessions are**
	* in order to make use of file-based sessions, you'll need to set the SESSION\_ENGINE setting to **django.contrib.sessions.backends.file**

* Explain Django URLS
	*  Django allows you design your own URLs
	* you'll need to create a python module called a **URLconf** or **url configuration, usually in the form of 'urls.py'**
	* the length of the above can be as long or short as required as well as reference other mappings
	* when a request is being processed, the requested URL is matched with the URLs present in **urls.py**, and the corresponding view is retrieved.

* is django a CMS?
	* No, django is not a CMS or any other 'turnkey product'
	* django would be the tool used to create a CMS

* how do you alter the Django admin page?
	* you can write specialized views for the admin page

* Write a simple Django view
	* ![[./_resources/Django_Interview_Questions.resources/unknown_filename.4.png]]

* what if you cannot log into the admin panel with the right credentials and no error message appears indicating wrong creds
	* the **login cookie** is likely not sit correctly
		* this happens if the domain of the cookie sent out by Django does not match the domain in your browser
		* change **SESSION\_COOKIE\_DOMAIN** setting to match that of the browser

* how can you see the raw SQL queries that Django runs?
	* make sure **DEBUG** is set to **True**
	* **type:**
		* **from django.db import connection**
		* **connection.queries** and hit Return

* is it mandatory to use the model/database layer
	* the model and database layer are actually decoupled from the rest of the framework

* How do you make a variable available to all templates
	* use teh **RequestContext**  in case all your templates require the same object
	* this method takes an **HttpRequest** as its first parameter and automatically populates the context within a few variables

* Does django support multiple-column primary keys
	* no; django only supports single-column primary keys
