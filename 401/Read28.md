# Django CRUD and Forms


## Django Forms

- Forms: a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server.
- Django takes a lot of the work out of creating forms. 
- Example of a simple HTML form:
```
<form action="/team_name_url/" method="post">
    <label for="team_name">Enter name: </label>
    <input id="team_name" type="text" name="name_field" value="Default name for team.">
    <input type="submit" value="OK">
</form>
```
- action: The resource/URL where data is to be sent for processing when the form is submitted.
- POST should be used when the data results in some kind of change to the server's database (this helps protect against cross-site forgery request attacks. 
- GET should be used for things like searches, or things that do not result in a change to the database. 
- Form class: simplifies both generation of form HTML and data cleaning/validation.
- Very basic Django form example:
```
from django import forms

class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")
```
- Common arguments to most fields:
```
REQUIRED: If True, the field may not be left blank or given a None value. Fields are required by default, so you would set required=False to allow blank values in the form.
LABEL: The label to use when rendering the field in HTML. If a label is not specified, Django will create one from the field name by capitalizing the first letter and replacing underscores with spaces (e.g. Renewal date).
LABEL_SUFFIX: By default, a colon is displayed after the label (e.g. Renewal date:). This argument allows you to specify a different suffix containing other character(s).
INITIAL: The initial value for the field when the form is displayed.
WIDGET: The display widget to use.
HELP_TEXT: Additional text that can be displayed in forms to explain how to use the field.
ERROR_MESSAGES: A list of error messages for the field. You can override these with your own messages if needed.
VALIDATORS: A list of functions that will be called on the field when it is validated.
LOCALIZE: Enables the localization of form data input (see link for more information).
DISABLED: The field is displayed but its value cannot be edited if this is True. The default is
```
- Example of cleaning data:
```
import datetime

from django import forms
from django.core.exceptions import ValidationError
from django.utils.translation import ugettext_lazy as _

class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")

    def clean_renewal_date(self):
        data = self.cleaned_data['renewal_date']

        # Check if a date is not in the past.
        if data < datetime.date.today():
            raise ValidationError(_('Invalid date - renewal in past'))

        # Check if a date is in the allowed range (+4 weeks from today).
        if data > datetime.date.today() + datetime.timedelta(weeks=4):
            raise ValidationError(_('Invalid date - renewal more than 4 weeks ahead'))

        # Remember to always return the cleaned data.
        return data
```
- URL config for the renew books page:
```
urlpatterns += [
    path('book/<uuid:pk>/renew/', views.renew_book_librarian, name='renew-book-librarian'),
]
```
- Function to decide we will be using GET to get the initial form or POST to actually post data to the database or return form with errors:
```
def renew_book_librarian(request, pk):
    book_instance = get_object_or_404(BookInstance, pk=pk)

    # If this is a POST request then process the Form data
    if request.method == 'POST':

        # Create a form instance and populate it with data from the request (binding):
        form = RenewBookForm(request.POST)

        # Check if the form is valid:
        if form.is_valid():
            # process the data in form.cleaned_data as required (here we just write it to the model due_back field)
            book_instance.due_back = form.cleaned_data['renewal_date']
            book_instance.save()

            # redirect to a new URL:
            return HttpResponseRedirect(reverse('all-borrowed') )

    # If this is a GET (or any other method) create the default form.
    else:
        proposed_renewal_date = datetime.date.today() + datetime.timedelta(weeks=3)
        form = RenewBookForm(initial={'renewal_date': proposed_renewal_date})

    context = {
        'form': form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)
```
- use @login_required to require that the user is logged in.
- Template example:
```
    {% extends "base_generic.html" %}

{% block content %}
  <h1>Renew: {{ book_instance.book.title }}</h1>
  <p>Borrower: {{ book_instance.borrower }}</p>
  <p{% if book_instance.is_overdue %} class="text-danger"{% endif %}>Due date: {{ book_instance.due_back }}</p>

  <form action="" method="post">
    {% csrf_token %}
    <table>
    {{ form.as_table }}
    </table>
    <input type="submit" value="Submit">
  </form>
{% endblock %}
```
- {% csrf_token %} reduces the chance of forms being hijacked by malicious users.
- Example using ModelForm:
```
from django.forms import ModelForm

from catalog.models import BookInstance

class RenewBookModelForm(ModelForm):
    class Meta:
        model = BookInstance
        fields = ['due_back']
```