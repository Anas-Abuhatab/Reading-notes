# Django REST Framework & Docker

## Beginner’s Guide to Docker
- Docker: what to isolate and run applications.
- The entire environment is isolated. 
- No longer need virtual environemtns. 
- Docker is really just linux containers. 
- Downside to virtual machine: size and speed.
- Virtual environments are used to isolate Python software packages locally.
- Virtual environments are more limited compared to Docker containers.

- use docker info to inspect.
- Only running containers will appear with docker container ls
- Images and containers are the two fundamental concepts to grasp when you start with Docker.
  - image: snapshot in time of what a project contains. 
  - container: running instance of the image.

- Dockerfile: a list of all requirements needed to build our image. 
- Dockerfiles are read from top-to-bottom. 
- Command to build image: docker image build .
- When a change is made to a step, all steps following it will be executed from scratch.
- It is better to put code that will not change at the top and code that will change towards the end. 
- docker-compose.yml: list of container instructions. 
- docker-compose.yml controls how to run the container.

## Django for APIs - Library Website
- Django REST Framework can only be added after Django project has already been initialized. 
- Django REST Framework creates web APIs which are a collection of URL endpoints containing available HTTP verbs that return JSON.
- Django file fuctions:
```
__init__.py is a Python way to treat a directory as a package; it is empty
asgi.py stands for Asynchronous Server Gateway Interface and is a new option in Django 3.0+
settings.py contains all the configuration for our project
urls.py controls the top-level URL routes
wsgi.py stands for Web Server Gateway Interface and helps Django serve the eventual web pages
manage.py executes various Django commands such as running the local web server or creating a new app.
```
- Each web page in traditional Django requires several files: a view, url, and template. But first we need a database model so let’s start there.
- Model example:
```
# books/models.py
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=250)
    subtitle = models.CharField(max_length=250)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)

    def __str__(self):
        return self.title
```
- The views.py file controls how the database model content is displayed. Example of a view:
```
# books/views.py
from django.views.generic import ListView
from .models import Book


class BookListView(ListView):
    model = Book
    template_name = 'book_list.html'
```
- After installing django rest framework, add in confid/settings.py:
```
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework', # new

    # Local
    'books',
]
```
- Add an API endpoint in config/urls.py:
```
# config/urls.py
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('api.urls')), # new
    path('', include('books.urls')),
]
```
- API views file:
```
# api/views.py
from rest_framework import generics

from books.models import Book
from .serializers import BookSerializer


class BookAPIView(generics.ListAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializer
```
- A serializer translates data into a format that is easy to consume over the internet, typically JSON, and is displayed at an API endpoint.
- Example of serializers file:
```
# api/serializers.py
from rest_framework import serializers

from books.models import Book


class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = ('title', 'subtitle', 'author', 'isbn')
```