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
# Django Install
Set up your development structure:



```
$ mkdir django_project      # here create folder the 
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

# Database settings
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

## For PostgreSQL
First your OS instll PostgresSQL then setup project

```
(venv)$  pip3 install django psycopg2     #Install package

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

Launch the development server:

```
(venv)$ python manage.py runserver
```













