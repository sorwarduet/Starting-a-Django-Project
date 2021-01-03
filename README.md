# Starting-a-Django-Project

## Setup
What you need for a basic Django dev environment:

  1. Python 2.7.x or 3.5.x
  2. easy_install and Pip
  3. Git
  4. virtualenv
  5. Database (SQLite, MySQL, PostgreSQL, MongoDB, etc.)
  6. Text editor (Sublime, VS Code,Notepat++ ...)

# Python 
Linux os. To check your Python version, run the command:

```
 $ python -V
 Python 3.8.5

```
if not install, download and install the latest version specific to your operating system.

# Git

For version control, we’ll be using git. You can check your current version, 
if you have git already installed, with the following command:

```
$ git --version
git version 2.25.1
```
If you do not have a git please installed


# virtualenv

It’s common practice to use a virtualenv (virtual environment) for your Python projects in order to create self-contained development environments (also called “sandboxes”). The goal of virtualenv is to prevent different versions of libraries/packages from messing with each other.

```
 $ pip install virtualenv
 or
 $ pip3 install virtualenv

```

## Local Setup Project Setup using Cookiecutter Django
https://cookiecutter-django.readthedocs.io/en/latest/developing-locally.html

1. Create a virtualenv:
```
$ virtualenv venv --python=python3.8
```
2. Activate the virtualenv you have just created:
```
$ source venv/bin/activate
```
3. Install cookiecutter package
```
$ pip install "cookiecutter>=1.7.0"
```
4. Now run it against this repo:

```
(venv)$ cookiecutter https://github.com/pydanny/cookiecutter-django.git
```
Answer the prompts with your own desired options. For example:

```
Cloning into 'cookiecutter-django'...
remote: Counting objects: 550, done.
remote: Compressing objects: 100% (310/310), done.
remote: Total 550 (delta 283), reused 479 (delta 222)
Receiving objects: 100% (550/550), 127.66 KiB | 58 KiB/s, done.
Resolving deltas: 100% (283/283), done.
project_name [Project Name]: Reddit Clone
project_slug [reddit_clone]: reddit
author_name [Daniel Roy Greenfeld]: Daniel Greenfeld
email [you@example.com]: pydanny@gmail.com
description [Behold My Awesome Project!]: A reddit clone.
domain_name [example.com]: myreddit.com
version [0.1.0]: 0.0.1
timezone [UTC]: America/Los_Angeles
use_whitenoise [n]: n
use_celery [n]: y
use_mailhog [n]: n
use_sentry [n]: y
use_pycharm [n]: y
windows [n]: n
use_docker [n]: n
use_heroku [n]: y
use_compressor [n]: y
Select postgresql_version:
1 - 12.3
2 - 11.8
3 - 10.8
4 - 9.6
5 - 9.5
Choose from 1, 2, 3, 4, 5 [1]: 1
Select js_task_runner:
1 - None
2 - Gulp
Choose from 1, 2 [1]: 1
Select cloud_provider:
1 - AWS
2 - GCP
3 - None
Choose from 1, 2, 3 [1]: 1
custom_bootstrap_compilation [n]: n
Select open_source_license:
1 - MIT
2 - BSD
3 - GPLv3
4 - Apache Software License 2.0
5 - Not open source
Choose from 1, 2, 3, 4, 5 [1]: 1
keep_local_envs_in_vcs [y]: y
debug[n]: n

Enter the project and take a look around:

$ cd reddit/
$ ls
```
Create a git repo and push it there:
```
$ git init
$ git add .
$ git commit -m "first awesome commit"
$ git remote add origin git@github.com:pydanny/redditclone.git
$ git push -u origin master


```


# Django Install
Set up your development structure:



```
$ mkdir django_project      # here create folder the 
$ python3 -m virtualenv yourenv  # For create virtualenv
$ virtualenv venv --python=python3.7
$ cd django_project
$ virtualenv venv           # here create virtualenv name is venv
$ source venv/bin/activate  # Active the virtualenv

```
Let’s get Django installed:

```
(venv)$ pip install django==3.0.* 
  or
(venv)$ pip3 install django==3.0.*

(venv)$ django-admin startproject core # here core is project name
```

#Project structures

```
core
├── core
│   ├── asgi.py
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-38.pyc
│   │   └── settings.cpython-38.pyc
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── manage.py
```

## pip freeze

Now that all your libraries are installed, use the following command to create a record of the installed libraries within the project directory

```
(venv)$ pip3 freeze > requirements.txt
For install
(venv)$ pip3 install -r requirements.txt
```


Launch the development server:

```
(venv)$ python manage.py runserver
```



## settings.py setup for Database, static, template, Login and Logout url


### Database settings
Default django setup SQLite

```
# Database
# https://docs.djangoproject.com/en/3.0/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}

```
If setup others database Example MySQL, PostgreSQL need to change Database.

### For PostgreSQL
First your OS instll PostgresSQL then setup project
if any version error local this commat use

```
$ sudo apt-get update
$ sudo apt-get install -y python3.5-dev
$ sudo apt-get install -y libpq-dev
```


```
(venv)$  pip3 install  psycopg2     #Install package

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'myproject',      # database name
        'USER': 'myprojectuser',  # database user name
        'PASSWORD': 'password',   # password
        'HOST': 'localhost',
        'PORT': '',
    }
}

```

### Static and template settings

```

......
import os

# Build paths inside the project like this: os.path.join(BASE_DIR, ...)
BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# local folder

TEMPLATE_DIR = os.path.join(BASE_DIR, 'templates')  # For template
STATIC_DIR = os.path.join(BASE_DIR, 'static')       # For static 
MEDIA_DIR = os.path.join(BASE_DIR, 'media')         # For media 



TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [ TEMPLATE_DIR, ],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]


STATIC_URL = '/static/'
STATICFILES_DIRS = [STATIC_DIR, ]
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')  # For admin static file

# For media file
MEDIA_URL = '/media/'
MEDIA_ROOT = MEDIA_DIR

```


# url.py setup
```
from django.contrib import admin
from django.urls import path, include
# For static file

from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),

]+static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```





# backup project database 

## Installation 

```
(venv)$ pip install django-dbbackup

```

## Add it in your project

In your settings.py, make sure you have the following things:

```
INSTALLED_APPS = (
    ...
    'dbbackup',  # django-dbbackup
)

DBBACKUP_STORAGE = 'django.core.files.storage.FileSystemStorage'
DBBACKUP_STORAGE_OPTIONS = {'location': os.path.join(BASE_DIR, 'backup')}

```

## Testing that everything worked
Now, you should be able to create your first backup by running:
```
 (venv)$ python manage.py dbbackup
```

## Restore a database. ::

```
 (venv)$ python manage.py dbrestore
```

https://django-dbbackup.readthedocs.io/en/master/commands.html


# Using dumpdata

Backup
```
python manage.py dumpdata --exclude auth.permission --exclude contenttypes > db.json

```


Loaddata
```
python manage.py loaddata db.json

```


