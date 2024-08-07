# Creating a new app in django

### Step 1: Create a new app

__Do not copy the code below. This is just a syntax__
```bash
python manage.py startapp <app_name>
```
example
```bash
python manage.py startapp main_app
```

### Step 2: Add the app to the project

Add the app to the `INSTALLED_APPS` in the `settings.py` file inside the `config` folder.

__Do not copy the code below. This is just a syntax.__
```python
INSTALLED_APPS = [
    ...
    '<app_name>',
]

```
for example, to add the `main_app` app to the project, the `INSTALLED_APPS` should look like this
```python
INSTALLED_APPS = [
    ...
    'main_app',
]
```

### Step 3: Create the views

Create the views in the `views.py` file inside the app folder.

__Do not copy the code below. This is just a syntax.__
```python

def <view_name>(request):
    # Logic goes here
    return render(request, '<template_name>.html',{
        'key1': value1, 'key2': value2
    })
```
example: if the view name is `index` and the template name is `index.html`, the code should look like this

```python
from django.shortcuts import render

def index(request):
    return render(request, 'index.html')
```

### Step 4: Create the urls

Create the urls in the `urls.py` file inside the app folder.

__Do not copy the code below. This is just a syntax.__
```python
urlpatterns = [
    path('<url>', views.<view_name>, name='<name>'),
]
```
example: if the url is `/` and the view name is `index`, the code should look like this
```python
from django.urls import path
from . import views

urlpatterns = [
    ...
    path('', views.index, name='index'),
]
```

### Step 5: Create the templates

Create the templates in the `templates` folder inside the app folder.

```
main_app/
    templates/
        <filename>.html
```
### Step 6: Run the server (if not already running)

Run the server to see the changes.

```bash
python manage.py runserver
```
