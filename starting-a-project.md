# Creating a new Django project

Commands and steps when creatign a new Django project

## Create a Django project
1) Move to desired directory to create your Django project
```
django-admin startproject ProjectName
```
2) Run migration to configure the database used by the default apps
```
cd ProjectName

python3 manage.py migrate
```

## Launch Django Project
Runs Django project on localhost (http://127.0.0.1:8000/)
````
python3 manage.py runserver
````

## Create a Django app
1) Inside the project root directory, ProjectName/, create an app by running:
````
python3 manage.py startapp appName
````
2) Add our new app to the list of installed apps for your Django project:

    1) Open settings.py inside your django project and find the list named "INSTALLED_APPS" and add the config file for
your appName by including ```'appName.apps.appNameConfig'``` to the list.
   ````ProjectName/ProjectName/settings.py````
    ````
   INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'appName.apps.appNameConfig'
    ]
    ````
## Create a Template
Create a HTML template file that will be used to display your app in the browser
1) Create a template directories to namespace the template
   1) Inside the project app directory ````appName/````, create a folder named ````templates/````
   2) Create a folder named after your app to namespace your template:
      - Example: ````appName/templates/appName/````
2) Within the namespaced template folder insert all your HTML files for your webpage.
   - Example: ````appName/templates/appName/filename.html````
