# Django Custom User

## Django Custum User Model
- Django ships with a built-in User model for authentication. 
- Use a custom user model instead for real world projects.
- setup steps:
  - create and navigate into a dedicated directory called accounts for our code
  - install Django
  - make a new Django project called config
  - make a new app accounts
  - start the local web server
- Commands:
```
$ cd ~/Desktop
$ mkdir accounts && cd accounts
$ pipenv install django~=3.1.0
$ pipenv shell
(accounts) $ django-admin.py startproject config .
(accounts) $ python manage.py startapp accounts
(accounts) $ python manage.py runserver
```
- wait until after we've created our new custom user model before migrating data.
- AbstractUser subclasses AbstractBaseUser but provides more default configuration.
- four steps for creating initial custom user model:
  - update config/settings.py
  - create a new CustomUser model
  - create new UserCreation and UserChangeForm
  - update the admin
- config settings file:
```
# config/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'accounts', # new
]
...
AUTH_USER_MODEL = 'accounts.CustomUser' # new
```
- add the model:
```
# accounts/models.py
from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    pass
    # add additional fields in here

    def __str__(self):
        return self.username
```
- Subclass existing forms:
```
# accounts/forms.py
from django import forms
from django.contrib.auth.forms import UserCreationForm, UserChangeForm
from .models import CustomUser

class CustomUserCreationForm(UserCreationForm):

    class Meta:
        model = CustomUser
        fields = ('username', 'email')

class CustomUserChangeForm(UserChangeForm):

    class Meta:
        model = CustomUser
        fields = ('username', 'email')
```
- Update admin file:
```
# accounts/admin.py
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin

from .forms import CustomUserCreationForm, CustomUserChangeForm
from .models import CustomUser

class CustomUserAdmin(UserAdmin):
    add_form = CustomUserCreationForm
    form = CustomUserChangeForm
    model = CustomUser
    list_display = ['email', 'username',]

admin.site.register(CustomUser, CustomUserAdmin)
```

## DjangoX
- Install DjangoX by cloning first:
```
$ git clone https://github.com/wsvincent/djangox.git
$ cd djangox
```
- Install via Pip:
```
$ python3 -m venv djangox
$ source djangox/bin/activate
(djangox) $ pip install -r requirements.txt
(djangox) $ python manage.py migrate
(djangox) $ python manage.py createsuperuser
(djangox) $ python manage.py runserver
# Load the site at http://127.0.0.1:8000
```
- Setup:
```
# Run Migrations
(djangox) $ python manage.py migrate

# Create a Superuser
(djangox) $ python manage.py createsuperuser

# Confirm everything is working:
(djangox) $ python manage.py runserver

# Load the site at http://127.0.0.1:8000
```