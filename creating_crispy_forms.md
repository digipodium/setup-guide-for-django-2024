# Django model forms
### (if not added) Add the module to the installed apps in the `settings.py` file
```python

INSTALLED_APPS = [
    ...
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'accounts',
    ...
]
```

### ❶ (if not created) Create a model in the `models.py` file of the app
```python
# models.py
from django.db import models
from django.contrib.auth.models import User

class Profile(models.Model):
    gender_choices = [
        ('male', "Male"),
        ('female', "Female"),
        ('other', "Dont want to disclose")
    ]
    first_name = models.CharField(max_length=50)
    last_name = models.CharField(max_length=50)
    picture= models.ImageField(upload_to='profile/')
    gender = models.CharField(max_length=10, choices=gender_choices)
    bio = models.TextField()
    user = models.OneToOneField(User, on_delete=models.CASCADE)

```

### ❷ Execute the following command to migrate your model to the database
- Check if the model is valid for the database
```bash
python manage.py makemigrations
```
- Apply the migration to the database
```bash
python manage.py migrate
```

### ❸ Create a model form in the `forms.py` file of the app. Model forms are directly linked to the model (table)
```python
# forms.py
from django import forms
from .models import Profile

class ProfileForm(forms.ModelForm):
    class Meta:
        model = Profile
        fields = ['first_name', 'last_name', 'picture','gender', 'bio']
```

### ❹ Create a view in the `views.py` file of the app
```python
# views.py
from django.shortcuts import render, redirect
from .forms import ProfileForm

def create_profile(request):
    if request.method == 'POST':
        form = ProfileForm(request.POST, request.FILES) # filled form
        if form.is_valid():
            form.save()
            return redirect('home')
    else:
        form = ProfileForm() # empty form
    return render(request, 'accounts/create_profile.html', {'form': form})
```

### ❺ Create a path in the `urls.py` file of the app
```python   
# urls.py
from django.urls import path
from . import views

urlpatterns = [
    ...
    path('profile/create', views.create_profile, name='create_profile'),
    ...
]
``` 

### ❻ Create a html template in the `templates` folder of the app
```html
<!-- create_profile.html -->
<form method="post" enctype="multipart/form-data">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Create</button>
</form>
```