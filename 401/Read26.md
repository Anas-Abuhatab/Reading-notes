# Intro to Django

## Getting started with Django How Django Works Behind the Scenes
- Object relational mapper: Define your data model in Python! Example:
```
class Band(models.Model):
    """A model of a rock band."""
    name = models.CharField(max_length=200)
    can_rock = models.BooleanField(default=True)


class Member(models.Model):
    """A model of a rock band member."""
    name = models.CharField("Member's name", max_length=200)
    instrument = models.CharField(choices=(
            ('g', "Guitar"),
            ('b', "Bass"),
            ('d', "Drums"),
        ),
        max_length=1
    )
    band = models.ForeignKey("Band")
```
- URLs and views: contains a simple mapping between URL patterns and your views. Example:
```
from django.urls import path

from . import views

urlpatterns = [
    path('bands/', views.band_listing, name='band-list'),
    path('bands/<int:band_id>/', views.band_detail, name='band-detail'),
    path('bands/search/', views.band_search, name='band-search'),
]
```
- Templates: Comfortable way to work with HTML. Devs can augment the template language as needed. Example:
```
<html>
  <head>
    <title>Band Listing</title>
  </head>
  <body>
    <h1>All Bands</h1>
    <ul>
    {% for band in bands %}
      <li>
        <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
        {% if band.can_rock %}<p>This band can rock!</p>{% endif %}
      </li>
    {% endfor %}
    </ul>
  </body>
</html>
```
- Forms: Django provides a powerful form library that handles rendering forms as HTML, validating user-submitted data, and converting that data to native Python types. Example:
```
from django import forms

class BandContactForm(forms.Form):
    subject = forms.CharField(max_length=100)
    message = forms.CharField()
    sender = forms.EmailField()
    cc_myself = forms.BooleanField(required=False)
```
- Authentication: handles user accounts, groups, permissions and cookie-based user sessions. Example:
```
from django.contrib.auth.decorators import login_required
from django.shortcuts import render

@login_required
def my_protected_view(request):
    """A view that can only be accessed by logged-in users"""
    return render(request, 'protected.html', {'current_user': request.user})
```
- Admin: reads metadata in your models to provide a powerful and production-ready interface that content producers can immediately use to start managing content on your site. Example: 
```
from django.contrib import admin
from bands.models import Band, Member

class MemberAdmin(admin.ModelAdmin):
    """Customize the look of the auto-generated admin for the Member model"""
    list_display = ('name', 'instrument')
    list_filter = ('band',)

admin.site.register(Band)  # Use the default options
admin.site.register(Member, MemberAdmin)  # Use the customized options
```
- Internationalization: lets developers and template authors specify which parts of their apps should be translated or formatted for local languages and cultures, and it uses these hooks to localize Web applications for particular users according to their preferences. Example: 


- Security: Django provides protection against:
    1. Clickjacking
    2. Cross-site scripting
    3. Cross Site Request Forgery (CSRF)
    4. SQL injection
    5. Remote code execution


## How Django Works Behind the Scenes

- Open sources packages like Django require some degree of funding. There are generally three ways that this happens:
  1. Corporate Sponsor: A group of engineers for a for-profit company are paid in part to upkeep the open source code. 
  2. Solo: The code is maintained/managed by a single developer. Funding sources can vary (examples are add-on or consulting services).
  3. Non-profit: This was actually Django's approach early on.
- Django Software Foundation does many things to maintain the service.
- Fellows Program: Largest DSF expense where paid contractors who triage tickets. This is necessary to keep Django on track. 