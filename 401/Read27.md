# Django Models

## Using Models
- Models define the structure of stored data
- It makes sense to separate models for each different object. For example, in. library example, we have books, book instances, and authors. 
- Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).
- Models are usually defined in an application's models.py file.
- Example of a "typical" model, named MyModelName:
```
from django.db import models

class MyModelName(models.Model):
    """A typical class defining a model, derived from the Model class."""

    # Fields
    my_field_name = models.CharField(max_length=20, help_text='Enter field documentation')
    ...

    # Metadata
    class Meta:
        ordering = ['-my_field_name']

    # Methods
    def get_absolute_url(self):
        """Returns the url to access a particular instance of MyModelName."""
        return reverse('model-detail-view', args=[str(self.id)])

    def __str__(self):
        """String for representing the MyModelName object (in Admin site etc.)."""
        return self.my_field_name
```
- Each field represents a column of data that we want to store in one of our database tables.
- Arguments being given in the article example for field:
```
max_length=20 — States that the maximum length of a value in this field is 20 characters.
help_text='Enter field documentation' — provides a text label to display to help users know what value to provide when this value is to be entered by a user via an HTML form.
```
- Some common field arguments:
  - help_text
  - verbose_name
  - default
  - null
  - blank
  - choices
  - primary_key
- Some common field types:
  - CharField
  - TextField
  - IntegerField
  - DateField/DateTimeField
  - EmailField
  - FileField/ImageField
  - AutoField
  - Foreign Key
  - ManyToManyField 
- Declare model-level metadata for your Model by declaring class Meta:
```
class Meta:
    ordering = ['-my_field_name']
```
- you can prefix the field name with a minus symbol (-) to reverse the sorting order.
