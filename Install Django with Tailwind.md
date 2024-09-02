1. First we have to Install Python to our system. To install Python we have to go https://www.python.org and download installer and install it.
2. After install create a folder to any drive. Open Command Prompt to this folder and create Virtual Environment by this command ```
```cmd
python -m venv .venv
```

3. To activate this Environment.
```cmd
.venv\Scripts\activate
```

4. Install Django to this virtual environment by this command

```cmd
pip install Django
```
5. Now we have to create Project using this command. Last portion will be Project Name We can give this as your requirement.

```cmd
django-admin startproject smartproject
```

6.  Migrate Database
```cmd
python manage.py migrate
```

7. Create Super User
```
python manage.py createsuperuser
```

Now our Django project is Ready to Run. We have to take access by activated virtual environment command prompt project file by `cd smartproject` where *mange.py* file is created and give this command.

```cmd
python manage.py runserver
```

Now our Django Project will run. As usual is run with http://127.0.0.1:8000/
it can be deferent port. We can select empty port like

```cmd
python manage.py runserver 8001
```

Now we have to install Node.js to our PC. Just Download https://nodejs.org/en/download/prebuilt-installer and install it.

Now go to Project folder and activate Virtual Environment and Follow the step.
```cmd
python -m pip install django-tailwind
```

If we want Hot Reload we can use another package.
``` cmd
//// most of the time it will show error. then use second one
python -m pip install 'django-tailwind[reload]'

//// it work for me
python -m pip install git+https://github.com/timonweb/django-tailwind.git
```

Now we have to make some setting in *setting.py* created in our project folder.

```python
INSTALLED_APPS = [
  # other Django apps
  'tailwind',
]
TAILWIND_APP_NAME = 'theme'
INTERNAL_IPS = [ "127.0.0.1", ]
NPM_BIN_PATH = r"C:\Program Files\nodejs\npm.cmd"

MIDDLEWARE = [
  # other Middleware
  "django_browser_reload.middleware.BrowserReloadMiddleware",
]
```

Now Create Tailwind them
```cmd
python manage.py tailwind init
```

Add to *setting.py*
```python
INSTALLED_APPS = [
  # other Django apps
  'theme',
]
```

Install Tailwind
```cmd
python manage.py tailwind install
```

Run this command to install Reload Packages
```cmd
pip install django-browser-reload
```

Add to *setting.py*
```python
INSTALLED_APPS = [
  # other Django apps
  'django_browser_reload',
]
```
add this code to *urls.py*
```python
from django.contrib import admin  
from django.urls import path, include  
  
from . import views  
  
urlpatterns = [  
    path('admin/', admin.site.urls),  
    path('', views.index, name='index'),  
  
    path("__reload__/", include("django_browser_reload.urls")),  
]
```

Make a views.py file in main project folder and and this code
```python
from django.shortcuts import render      
def index(request):  
    return render(request, 'base.html')
```

Now run this scripts
```cmd
python manage.py tailwind start
```


Go to the http://127.0.0.1:8000/ We will see below picture is everything ok.  if we did not show that then there is some thing wrong
![[Screenshot_1.jpg]]


Finished..... Now we can develop our project using this template.

Make requirements file. first activate Virtual Environment to make used packages

```cmd
pip freeze --local > requirements.txt
```

Install requirements.txt

```
pip install -r requirements.txt
```