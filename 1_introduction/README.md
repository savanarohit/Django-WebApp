# Django Web Framework Introduction

Django is a high-level Python web framework that follows the Model-View-Controller (MVC) architectural pattern. It provides a set of tools, libraries, and conventions that simplify the development of web applications. Django is known for its emphasis on simplicity, reusability, and the principle of "Don't Repeat Yourself" (DRY).

The Model-View-Controller (MVC) pattern is a design pattern commonly used in web application development.

1. Model: The model represents the data and the business logic of the application. It defines the structure of the data, handles data validation, and interacts with the database or any other data source. In Django, models are typically represented as Python classes that inherit from django.db.models.Model. They define the fields, relationships, and behavior of the data entities in the application.

2. View: The view handles the presentation logic and user interaction. It retrieves data from the model and decides how to present it to the user. In Django, views are Python functions or methods that receive HTTP requests, process them, and return HTTP responses. Views can render HTML templates, handle form submissions, authenticate users, and perform other tasks related to generating the appropriate response for a given request.

3. Controller: In the MVC pattern, the controller acts as an intermediary between the model and the view. It receives user input from the view, processes it, and updates the model accordingly. However, in Django, the concept of the controller is merged with the view. Django's view functions or methods often handle both the presentation logic and the business logic, interacting directly with the model and returning the appropriate response.

## Creating Virtual Environments:

Pipenv: Pipenv is a tool for managing Python project dependencies and virtual environments. It combines the functionality of pip (package installation) and virtualenv (virtual environment creation) into a single tool. Pipenv aims to simplify dependency management by providing a streamlined workflow and automatic environment activation.

Installation: 

You can install Pipenv by running the following command:

    pip install pipenv

#### Creating a new project: 

To start a new project with Pipenv, navigate to the project's directory using the terminal and run the following command:

    pipenv --python 3.11

For Windows (GitBash prompt) - This creates a new virtual environment for the project, using Python 3.11 (replace with your desired Python version).

    python -m pipenv --python 3.11 

    Creating a virtualenv for this project...
    Pipfile: E:\onedrive\Rohit\certificates\eduonix\2_web_development_django\Pipfile
    Using C:/Python311/python.exe (3.11.0) to create virtualenv...
    [    ] Creating virtual environment...created virtual environment CPython3.11.0.final.0-64 in 11799ms
    creator CPython3Windows(dest=C:\Users\rohit\.virtualenvs\2_web_development_django-XOwsaMNC, clear=False, no_vcs_ignore=False, global=False)
    seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=C:\Users\rohit\AppData\Local\pypa\virtualenv)
    added seed packages: pip==23.1.2, setuptools==68.0.0, wheel==0.40.0
    activators BashActivator,BatchActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

    Successfully created virtual environment!
    Virtualenv location: C:\Users\rohit\.virtualenvs\2_web_development_django-XOwsaMNC
    Creating a Pipfile for this project...

#### Adding dependencies: 

To add a package dependency to your project, use the pipenv install command followed by the package name.

    pipenv install django     # This installs Django and automatically updates the Pipfile and Pipfile.lock files, which keep track of your project's dependencies.

For Windows

    python -m pipenv install django

    Installing django...
    Resolving django... 
    Adding django to Pipfile's [packages] ...
    Installation Succeeded
    Pipfile.lock not found, creating...
    Locking [packages] dependencies... 
    Building requirements...
    Resolving dependencies...
    Success!
    Locking [dev-packages] dependencies...
    Updated Pipfile.lock (59a064f055bfda3ad3323efe9a4c40d8b21d9cec899d72308e2abd62dbf0366f)!
    Installing dependencies from Pipfile.lock (f0366f)...
    To activate this project's virtualenv, run pipenv shell.
    Alternatively, run a command inside the virtualenv with pipenv run.

#### Activating the virtual environment: 

To activate the virtual environment and access the project's shell, run:

    pipenv shell        (This command activates the virtual environment and opens a new shell within it)

For Windows 

    python -m pipenv shell

#### Running Python scripts: 

Once inside the Pipenv shell, you can run Python scripts or interact with the installed packages as you would in a regular Python environment.

#### Deactivating the virtual environment: 

To exit the virtual environment and return to your system's default Python environment, use the exit command or press Ctrl + D.

#### Managing dependencies: 

Pipenv provides additional commands for managing dependencies. For example:

    pipenv install --dev                    # installs development dependencies.
    pipenv update                           # updates all packages to their latest compatible versions.
    pipenv lock                             # generates a lockfile (Pipfile.lock) with exact versions for all installed packages.

## Setting up Django for a feed webapp:

activate your virtual environment and check present working dir

    python -m pipenv shell

    pwd

## Create a Django project: 

This command create a mysite dir in current dir

    django-admin startproject mysite .         

mysite dir and manage.py file

The outer mysite/ root directory is a container for your project. Its name doesn’t matter to Django; you can rename it to anything you like.
manage.py: A command-line utility that lets you interact with this Django project in various ways. You can read all the details about manage.py in django-admin and manage.py.

mysite dir

    $ ls -l mysite/
    total 10
    -rw-r--r-- 1 rohit 197121    0 Jul 15 10:02 __init__.py
    -rw-r--r-- 1 rohit 197121  405 Jul 15 10:02 asgi.py    
    -rw-r--r-- 1 rohit 197121 3344 Jul 15 10:02 settings.py
    -rw-r--r-- 1 rohit 197121  784 Jul 15 10:02 urls.py    
    -rw-r--r-- 1 rohit 197121  405 Jul 15 10:02 wsgi.py    

    The inner mysite/ directory is the actual Python package for your project. Its name is the Python package name you’ll need to use to import anything inside it (e.g. mysite.urls).
    mysite/__init__.py: An empty file that tells Python that this directory should be considered a Python package. If you’re a Python beginner, read more about packages in the official Python docs.
    mysite/settings.py: Settings/configuration for this Django project. Django settings will tell you all about how settings work.
    mysite/urls.py: The URL declarations for this Django project; a “table of contents” of your Django-powered site. You can read more about URLs in URL dispatcher.
    mysite/asgi.py: An entry-point for ASGI-compatible web servers to serve your project. See How to deploy with ASGI for more details.
    mysite/wsgi.py: An entry-point for WSGI-compatible web servers to serve your project. See How to deploy with WSGI for more details.

Run the development server (We can also create alias for below command)

    python manage.py runserver

    Watching for file changes with StatReloader
    Performing system checks...

    System check identified no issues (0 silenced).
    July 15, 2023 - 10:23:59
    Django version 4.2.3, using settings 'mysite.settings'
    Starting development server at http://127.0.0.1:8000/ 
    Quit the server with CTRL-BREAK.

The production server . If you want to specify a different IP address or port number, you can pass them as arguments to the runserver command

    python manage.py runserver 0.0.0.0:8000

## Migrate:  

Migrations are a way to manage changes to your database schema over time, such as creating new tables, altering existing tables, or adding new columns. When you make changes to your Django models or create new models, Django generates migration files that contain the instructions for applying those changes to the database. These migration files are stored in the "migrations" directory of your Django app. By running python manage.py migrate, you tell Django to examine the migration files and apply any pending changes to the database. Django keeps track of which migrations have been applied, so it only applies new migrations that haven't been executed yet.

To migrate 

    python manage.py migrate

    Operations to perform:
    Apply all migrations: admin, auth, contenttypes, sessions
    Running migrations:
    Applying contenttypes.0001_initial... OK
    Applying auth.0001_initial... OK
    Applying admin.0001_initial... OK
    Applying admin.0002_logentry_remove_auto_add... OK     
    Applying admin.0003_logentry_add_action_flag_choices... OK
    Applying contenttypes.0002_remove_content_type_name... OK 
    Applying auth.0002_alter_permission_name_max_length... OK
    Applying auth.0003_alter_user_email_max_length... OK     
    Applying auth.0004_alter_user_username_opts... OK   
    Applying auth.0005_alter_user_last_login_null... OK
    Applying auth.0006_require_contenttypes_0002... OK
    Applying auth.0007_alter_validators_add_error_messages... OK
    Applying auth.0008_alter_user_username_max_length... OK     
    Applying auth.0009_alter_user_last_name_max_length... OK
    Applying auth.0010_alter_group_name_max_length... OK    
    Applying auth.0011_update_proxy_permissions... OK     
    Applying auth.0012_alter_user_first_name_max_length... OK
    Applying sessions.0001_initial... OK

Running python manage.py migrate performs the following steps:

    It checks for any new migration files that haven't been applied yet.
    It analyzes the migration files to determine the changes they represent.
    It modifies the database schema to match the changes described in the migration files.
    It updates the migration history, marking the applied migrations as completed.

Run the development server

    python manage.py runserver 

    Watching for file changes with StatReloader
    Performing system checks...

    System check identified no issues (0 silenced).
    July 15, 2023 - 10:23:59
    Django version 4.2.3, using settings 'mysite.settings'
    Starting development server at http://127.0.0.1:8000/ 
    Quit the server with CTRL-BREAK.

## Django Admin page:

To access Django admin page from your browser 

    http://127.0.0.1:8000/admin/

First we need to create username and password from command line

    python manage.py createsuperuser

    $ python manage.py createsuperuser
    Username (leave blank to use 'username'): username
    Email address: email_id@gmail.com
    Password:
    Password (again):

## Creating a new webapp:

python manage.py startapp feed

feed dir 

    $ ls -l feed/
    total 5
    -rw-r--r-- 1 rohit 197121   0 Jul 15 10:55 __init__.py
    -rw-r--r-- 1 rohit 197121  66 Jul 15 10:55 admin.py   
    -rw-r--r-- 1 rohit 197121 146 Jul 15 10:55 apps.py    
    drwxr-xr-x 1 rohit 197121   0 Jul 15 10:55 migrations 
    -rw-r--r-- 1 rohit 197121  60 Jul 15 10:55 models.py  
    -rw-r--r-- 1 rohit 197121  63 Jul 15 10:55 tests.py   
    -rw-r--r-- 1 rohit 197121  66 Jul 15 10:55 views.py  

models.py: This file defines the data models for your application. Models are Python classes that represent database tables and encapsulate the logic for interacting with the database. You define fields, relationships, and behaviors of your data in this file using Django's model field types and options.

views.py: This file contains the views of your application. Views are Python functions or classes that handle HTTP requests and generate responses. They define the logic for processing user requests, retrieving data from models, and rendering templates or returning JSON responses.

urls.py: This file defines the URL routing for your application. It maps URLs to the appropriate views that should handle them. You specify URL patterns and their corresponding view functions or classes in this file, allowing Django to determine which view to invoke based on the requested URL.

forms.py: This file is used for defining Django forms. Forms are used to handle user input and perform validation. By defining forms, you can generate HTML forms automatically from your model definitions or create custom forms with specific fields and validation logic.

admin.py: This file is used to register your models with the Django admin interface. The admin interface provides a convenient way to manage and interact with the data in your models. In this file, you can customize the appearance and behavior of the admin site and define how your models are displayed and edited.

templates/: This directory contains HTML templates used for rendering the views. Templates allow you to separate the presentation logic from the Python code. Django uses a templating engine to fill in dynamic data and generate HTML responses. The directory structure within the templates/ directory usually mirrors the app structure.

static/: This directory is used to store static files such as CSS, JavaScript, and image files. Django serves these files directly to the client without processing them. The structure within the static/ directory can also mirror the app structure.

migrations/: This directory contains database migration files. When you make changes to your models, Django generates migration files that define how to modify the database schema. These files are automatically created and managed by Django's migration framework.

Activate feed app

Go to mysite (project) dir and in settings.py and look for INSTALLED_APPS section. This is basically a list add feed in last like below.

    INSTALLED_APPS = [
        "django.contrib.admin",
        "django.contrib.auth",
        "django.contrib.contenttypes",
        "django.contrib.sessions",
        "django.contrib.messages",
        "django.contrib.staticfiles",
        "feed",
    ]

Migrate - To view changes, synchronize app with DB 

    python manage.py migrate

Run the development server

    python manage runserver

    $ python manage.py runserver
    Watching for file changes with StatReloader
    Performing system checks...

    System check identified no issues (0 silenced).
    July 15, 2023 - 11:32:12
    Django version 4.2.3, using settings 'mysite.settings'
    Starting development server at http://127.0.0.1:8000/ 
    Quit the server with CTRL-BREAK.

## Remove an app:

Make sure your Django development server is not running. If it is running, you can stop it by pressing Ctrl + C in the command prompt or terminal where it's running.

Locate the root directory of your Django project. This is the directory that contains the manage.py file.

Open a command prompt or terminal window and navigate to the root directory of your Django project.

Once you are in the project's root directory, execute the following command:

    python manage.py makemigrations --empty feed

Next, run the migration command to apply the empty migration:

    python manage.py migrate

This will remove the database tables associated with the "feed" app from the database.

After removing the database tables, you can delete the "feed" app directory from your project manually.

Finally, remove the "feed" app entry from the INSTALLED_APPS setting section in your project's settings.py file. 

## Creating a Model for feed app:

Model - a model is a Python class that represents a database table. It encapsulates the fields (data attributes) and behaviors (methods) of the data you want to store and manipulate within the database. By defining the model, you can perform various operations such as creating, updating, deleting, and querying the data stored in the corresponding database table. Django's ORM provides a rich set of methods and query APIs to perform these operations, making it easier to work with databases without writing raw SQL queries.

Go to models.py file in feed app and in create your models section create a Class as Post as below. Basically it is a Table with two columns.

    class Post(models.Model):
        text = models.CharField(max_length=140, blank=False, null=False)

Once you save this file Django will automatically reload the development server. Then run makemigrations command as below. It will create Tables with two columns in the database( SQLite by default)

    python manage.py makemigrations

    $ python manage.py makemigrations
    Migrations for 'feed':
    feed\migrations\0001_initial.py
        - Create model Post

This creates a 0001_initial.py in migrations dir of feed app

Now run migration command to add model (table) with two columns

    python manage.py migrate

    $ python manage.py migrate
    Operations to perform:
    Apply all migrations: admin, auth, contenttypes, feed, sessions
    Running migrations:
    No migrations to apply.

Now rerun the development server

    python manage.py runserver

This new Tables exists but it is not manageable. That is the reason it does not appear in Django admin page. To do this follow below steps.

Go to admin.py file in feed app dir. In Register your models here section add details as below with import too.

    from django.contrib import admin
    from .models import Post

    class PostAdmin(admin.ModelAdmin):
        pass

    admin.site.register(Post, PostAdmin)

## View: 

a view is a Python function or method that receives a web request and returns a web response. Views determine what data to retrieve from the database, how to process it, and which template to use to render the response. A view function takes the incoming request as its argument and typically returns an instance of the HttpResponse class or one of its subclasses.


Create View in feed webapp

Create a urls.py file in feed webapp dir and add below contents.

    from django.urls import path
    from .views import HomePageView

    app_name = "feed"
    urlpatterns = [path("", HomePageView.as_view(), name="index")]

In views.py file add below contents

    from django.views.generic import TemplateView

Create your views here.

    class HomePageView(TemplateView):
        template_name = "home.html"

Finally add below contents into mysite/urls.py file

    from django.contrib import admin
    from django.urls import path
    from django.conf.urls import include

    from feed import urls as feed_urls

    urlpatterns = [
        path("admin/", admin.site.urls),
        path("", include(feed_urls, namespace="feed")),

Go back to webpage and refresh it , you will an error - TemplateDoesNotExist at /home.html. It looks for this Template in below dirs.

django-webapp-T1MGwRR1\Lib\site-packages\django\contrib\admin\templates\home.html
django-webapp-T1MGwRR1\Lib\site-packages\django\contrib\auth\templates\home.html

## Template:

a template is a text file that defines the structure and presentation of a web page. It is a fundamental component of the Model-View-Controller (MVC) architectural pattern used by Django. Templates allow you to separate the design and layout of your web pages from the Python code that handles the application's logic. Django templates use a syntax called Django Template Language (DTL) or simply template tags. Template tags are enclosed in curly braces ({{ }}) or percent signs ({% %}) and allow you to insert dynamic content, perform logic, iterate over data, and include other templates.

Setting up Templates dir

Here's a basic example of a Django template:

    <!DOCTYPE html>
    <html>
    <head>
        <title>My Website</title>
    </head>
    <body>
        <h1>Hello, {{ name }}!</h1>
        <p>Today is {{ date }}</p>
    </body>
    </html>

In this example, the template includes HTML markup along with template tags. The {{ name }} and {{ date }} are template variables that will be replaced with actual values when the template is rendered. The rendering process takes place when a view function returns an HTTP response, and Django combines the template with the provided data.

Django templates offer various features, including:

Variables: You can insert variables into the template to display dynamic content. Variables are surrounded by double curly braces ({{ }}) and can be any valid Python expression.

Template tags: Template tags are used for performing logic and flow control in templates. They are enclosed in percent signs ({% %}) and allow you to iterate over data, conditionally render blocks of content, and include other templates.

Template filters: Filters allow you to modify the output of variables or apply formatting to data. Filters are used by chaining them with the pipe symbol (|) after a variable and provide additional functionality like date formatting, string manipulation, and more.

Inheritance and template inheritance: Templates can inherit from a base template and extend its content. This enables reusable templates and a modular approach to building web pages.

Setting up Templates dir for feed webapp

Go to setting.py in mysite dir. Search for TEMPLATES section and update as below.

    TEMPLATE_DIR = os.path.join(BASE_DIR,"templates")

    TEMPLATES = [
        {
            "BACKEND": "django.template.backends.django.DjangoTemplates",
            "DIRS": [TEMPLATE_DIR],
            "APP_DIRS": True,
            "OPTIONS": {
                "context_processors": [
                    "django.template.context_processors.debug",
                    "django.template.context_processors.request",
                    "django.contrib.auth.context_processors.auth",
                    "django.contrib.messages.context_processors.messages",
                ],
            },
        },
    ]

Also add import os at import section of the file in top. Then go back to page and check again you will see same error but this time dir is different.

django.template.loaders.filesystem.Loader: django-webapp\1_introduction\templates\home.html (Source does not exist)
django.template.loaders.app_directories.Loader: django-webapp-T1MGwRR1\Lib\site-packages\django\contrib\admin\templates\home.html (Source does not exist)
django.template.loaders.app_directories.Loader: django-webapp-T1MGwRR1\Lib\site-packages\django\contrib\auth\templates\home.html (Source does not exist)

Create a templates dir and in this add home.html file in this add h1 tag with Hello Django!. Now refresh the main page you will see Hello Django! 
If after refresh it is not working then restart django server.

How to handle when we have multiple views

Create a base.html file with html5 boilerplate and also create home.html page with no content in it.
Now in home.html file add {% extends "base.html" %} to call base.html content.

## Template blocks:

template blocks are a feature that allows you to define sections of a template that can be overridden or extended by child templates. Template blocks are used in conjunction with template inheritance to create modular and reusable templates.

Base Template (base.html):

    <!DOCTYPE html>
    <html>
    <head>
        <title>{% block title %}My Website{% endblock %}</title>
    </head>
    <body>
        {% block content %}
            <h1>Welcome to my website!</h1>
        {% endblock %}
    </body>
    </html>

Child Template (child.html):

    {% extends 'base.html' %}

    {% block title %}
        My Awesome Website
    {% endblock %}

    {% block content %}
        <h1>Welcome to my awesome website!</h1>
        <p>This website is amazing!</p>
    {% endblock %}

In this example, the base.html template serves as the base template that defines the common structure of the web pages. It contains two template blocks: title and content. The content inside these blocks acts as a placeholder and will be replaced or extended by child templates.

The child.html template extends the base.html template using the {% extends %} template tag. It then overrides the title and content blocks with its own content. When the child.html template is rendered, the content from the base.html template will be included, and the content of the blocks defined in the child template will replace the corresponding blocks in the base template.

When the child template is rendered, the resulting HTML will be:

    <!DOCTYPE html>
    <html>
    <head>
        <title>My Awesome Website</title>
    </head>
    <body>
        <h1>Welcome to my awesome website!</h1>
        <p>This website is amazing!</p>
    </body>
    </html>

Template blocks allow you to define sections of a template that can be customized and overridden in child templates. They provide a way to reuse common template code while allowing flexibility to modify or extend specific sections as needed. This modular approach to template design promotes code reuse, maintainability, and a clean separation of concerns.

Creating template block in base.html file. (title and body blocks)

    <html>
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <title>{% block title %} {% endblock %} </title>  
            <meta name="description" content="">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <link rel="stylesheet" href="">
        </head>
        <body>
            <!--[if lt IE 7]>
            <p class="browsehappy">You are using an <strong>outdated</strong> browser. Please <a href="##">upgrade your browser</a> to improve your experience.</p>
            <![endif]-->
            <script src="" async defer></script>
            
            {% block body %} {% endblock %}
        
        </body>
    </html>

Now first extends and then call both title and body block in home.html. blocks are like html tag - title , body etc.

    {% extends 'base.html' %}
    {% block title %} Title from home.html {% endblock %}
    {% block body  %}
        <h2>
        Stuff in here from home.html
        </h2>
    {% endblock %}

We can also have a default in base.html file. If someone forget to call title block in home.html file.

    <title>{% block title %} Default title {% endblock %}</title>

## Custom page context:

the page context refers to the data that is available to the template when it is rendered. By default, Django provides a context that includes variables and data from the view function or class. However, you can also customize the page context by adding additional data or modifying the existing context. Customizing the page context allows you to pass specific data to the template that is relevant to the current page or view. You can include any Python objects, such as variables, dictionaries, lists, querysets, or model instances, in the page context.