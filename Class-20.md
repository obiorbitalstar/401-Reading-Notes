# Django Models
Django web applications access and manage data through Python objects referred to as models. Models define the structure of stored data, including the field types and possibly also their maximum size, default values, selection list options, help text for documentation, label text for forms, etc. The definition of the model is independent of the underlying database — you can choose one of several as part of your project settings. Once you've chosen what database you want to use, you don't need to talk to it directly at all — you just write your model structure and other code, and Django handles all the dirty work of communicating with the database for you.

## Model definition 
Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata

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

## Model management 
Once you've defined your model classes you can use them to create, update, or delete records.

 ## Creating and modifying records
    ``` 
    # Create a new record using the model's constructor.
    record = MyModelName(my_field_name="Instance #1")

    # Save the object into the database.
    record.save()
    ```
    You can access the fields in this new record using the dot syntax, and change the values. You have to call save() to store modified values to the database.

    ```
    # Access model field values using Python attributes.
    print(record.id) # should return 1 for the first record. 
    print(record.my_field_name) # should print 'Instance #1'

    # Change record by modifying the fields, then calling save().
    Change record by modifying the fields, then calling save().
    record.my_field_name = "New Instance Name"
    record.save()
        
    ```


# Django admin site
Now that we've created models, we'll use the Django Admin site to add some data

The Django admin application can use your models to automatically build a site area that you can use to create, view, update, and delete records. This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data.

## Registering models 
First, open admin.py in the catalog application (/locallibrary/catalog/admin.py). It currently looks like this — note that it already imports django.contrib.admin:

``` 
from django.contrib import admin

# Register your models here.

```
Register the models by copying the following text into the bottom of the file. This code simply imports the models and then calls admin.site.register to register each of them.

```
admin.site.register(model1)
admin.site.register(model2)
admin.site.register(model3)
admin.site.register(model4)

```

## Creating a superuser

In order to log into the admin site, we need a user account with Staff status enabled. In order to view and create records we also need this user to have permissions to manage all our objects.  You can create a "superuser" account that has full access to the site and all needed permissions using manage.py.

``` 
# in the terminal 
python3 manage.py createsuperuser
python3 manage.py runserver

```
