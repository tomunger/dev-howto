# Notes

user 'admin' ps 'core'

# Reference
 * [Tech with Tim Django Tutorials](https://www.youtube.com/watch?v=9jDEnSm4nt8&list=PLzMcBGfZo4-kQkZp-j9PNyKq7Yw5VYjq9&index=6)
 * [Url Dispatcher](https://docs.djangoproject.com/en/3.0/topics/http/urls/)
 * [Database API](https://docs.djangoproject.com/en/3.0/topics/db/queries/)
 * [Related Objects](https://docs.djangoproject.com/en/3.0/ref/models/relations/)
 * [Template Guide](https://docs.djangoproject.com/en/3.0/topics/templates/)
 * [Mozilla tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django)
 * [Beginning Django](https://www.webforefront.com/django/)
 * [Django 20+ tutorials](https://data-flair.training/blogs/django-tutorials-home/)
 * [Django and bootstrap](https://tutorial.djangogirls.org/en/css/)
 * [Django with bootstrap and crispy-forms](https://simpleisbetterthancomplex.com/tutorial/2018/08/13/how-to-use-bootstrap-4-forms-with-django.html)

 * [Bootstrap Tutorial](http://www.java2s.com/Tutorials/HTML_CSS/Bootstrap_Tutorial/index.htm)
  
  

## Packages

 * [Django Packages](https://djangopackages.org)
 * [Ultimate Django](https://ultimatedjango.com/learn-django/chapters/)
  

# Commands

Install django

    virtualenv env
    pip install django

Start a project

    django-admin startproject <sitename>

Creates a project (`<sitename>`) and the first app with in that (`<sitename>/<sitename>`)

Create a second app

    python manage.py startapp <name>


Running the server

    python manage.py runserver <port>

Add your application to the project site in settings.py

    INSTALLED_APPS = [
        'polls.apps.PollsConfig',

# Add routing

 * site/urls.py - add entry to delegate routing `    path('bbapi/', include('bbapi.urls')),`
 * bbapi/urls.py - add entry for each url `path('', views.index, name='index')`
 * bbapi/views.py - add view definition `def index(request):`

# Model

Made changes to model, store those as a migration (in polls/migrations/*)

    python manage.py makemigrations polls

Apply the migration

    python manage.py migrate

Create user

    python manage.py createsuperuser
    

# Tutorial

[Next step](https://docs.djangoproject.com/en/3.0/intro/tutorial04/)

# Deploy

[Crispy forms](https://django-crispy-forms.readthedocs.io/en/latest/install.html) says to always activate Django Template cache loader


# Testing

## Unit tests

Run tests with

    python manage.py test



# User Management

## Add registration in page.

suggest building in it's own application so it is portable to other applications

However, rather than create urls.py in that application, reference page directly from project urls.py file:

    from usermgmt import views as userviews
    ...
    path('register/', userviews.register, name='regiseter'),


create a new form that inherits from `django.contrib.auth.forms` `UserCreationForm`.  Add email field and meta class.  Note reference to model User

	email = forms.EmailField()

	class Meta:
		model = User
		fields = ["username", "email", "password1", "password2"]

Create `register` view that resents our register form


## Add log in pages

Add 

    path('', include('django.contrib.auth.urls'))

Create a `registration` folder in templates (suggest the user management app).  Create a new file `login.html` and render form.

Login directs to `http://127.0.0.1:8000/accounts/profile/`.  Redirect with

LOGIN_REDIRECT_URL = "/"

# Writing API

use django REST api framework

# Handling Errors in production

On calls to get object use

    get_object_or_404()


# Production

## settings.py
Set `DEBUG` to `False`

Configure `ALLOWED_HOSTS`