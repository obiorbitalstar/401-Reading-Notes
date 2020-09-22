# Django Custom User Model 
Django ships with a built-in User model for authentication, however the official Django documentation highly recommends using a custom user model for new projects. The reason is if you want to make any changes to the User model down the road--for example adding a date of birth field--using a custom user model from the beginning makes this quite easy. But if you do not, updating the default User model in an existing Django project is very, very challenging.

# Setup
--> create a new Django project 
import note : do not migrate just yet after creating the project and the app 

# Custom User Model
creating initial user model requires four steps 
* update project/settings.py:
    In settings.py we'll add the accounts app and use the AUTH_USER_MODEL config to tell Django to use our new custom user model in place of the built-in User model. We'll call our custom user model CustomUser.
    ```
    #config/settings.py
    INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'accounts', # new
    ]

    
    AUTH_USER_MODEL = 'accounts.CustomUser' # new

    ```
    

* create a new CustomUser model: 
    Now update app/models.py with a new User model which we'll call CustomUser.

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
* create new UserCreation and UserChangeForm:
    create a new file in the accounts app called forms.py.
    We'll update it with the following code to largely subclass the existing forms.
    
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

    finally update the admin.py in the app folder 
    
    ```
    from django.contrib import admin
    from django.contrib.auth import get_user_model
    from django.contrib.auth.admin import UserAdmin

    from .forms import CustomUserCreationForm, CustomUserChangeForm
    from .models import CustomUser

    class CustomUserAdmin(UserAdmin):
        add_form = CustomUserCreationForm
        form = CustomUserChangeForm
        model = CustomUser
        list_display = ['email', 'username',]

    admin.site.register(CustomUser, CustomUserAdmin)     

and thats it, now you can run makemigrations and migrate 