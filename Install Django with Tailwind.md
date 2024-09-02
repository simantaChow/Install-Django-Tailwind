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
6. Now our Django project is Ready to Run. We have to take access by activated virtual environment command prompt project file by `cd smartproject` where *mange.py* file is created and give this command.
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
  'theme',
  'django_browser_reload',
]
TAILWIND_APP_NAME = 'theme'
INTERNAL_IPS = [ "127.0.0.1", ]
NPM_BIN_PATH = r"C:\Program Files\nodejs\npm.cmd"

MIDDLEWARE = [
  # other Middleware
  "django_browser_reload.middleware.BrowserReloadMiddleware",
]
```
Open *urls.py* file in project file and make create this path for hot reload.
```python
from django.urls import include, path
urlpatterns = [
    ...,
    path("__reload__/", include("django_browser_reload.urls")),
]
```
Now run this scripts one by one
```cmd
python manage.py tailwind init
python manage.py tailwind install
python manage.py tailwind start
```
