# Django: Forms

The form is defined in HTML as a collection of elements inside <form>...</form> tags, containing at least one input element of type="submit".

The submit input will be displayed as a button (by default) that can be pressed by the user to upload the data in all the other input elements in the form to the server,The form attributes define the HTTP method used to send the data and the destination of the data on the server (action):

* action: The resource/URL where data is to be sent for processing    when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.

* method: The HTTP method used to send the data: post or get.
    * The POST method should always be used if the data is going to result in a change to the server's database because this can be made more resistant to cross-site forgery request attacks.

    * The GET method should only be used for forms that don't change user data (e.g. a search form). It is recommended for when you want to be able to bookmark or share the URL.


# Django form handling process

## Declaring a Form

    ```
    from django import forms
    
    class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")

    ```

## Form fields
There are many other types of form fields, which you will largely recognize from their similarity to the equivalent model field classes:
 BooleanField, CharField, ChoiceField, TypedChoiceField, DateField, DateTimeField, DecimalField, DurationField, EmailField, FileField, FilePathField, FloatField, ImageField, IntegerField, GenericIPAddressField, MultipleChoiceField, TypedMultipleChoiceField, NullBooleanField, RegexField, SlugField, TimeField, URLField, UUIDField, ComboField, MultiValueField, SplitDateTimeField, ModelMultipleChoiceField, ModelChoiceField.

## Validation
Django provides numerous places where you can validate your data. The easiest way to validate a single field is to override the method clean_<fieldname>() for the field you want to check.

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
