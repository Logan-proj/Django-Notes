# Creating a new Django project

Commands and steps when creating a new Django project

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
In order to create templates, they have to be stored in the application in a folder called templates/. Another folder 
needs to be created inside of this templates/ folder that uses the same name of the application.
````
projectname/
 |-- appname/
     |-- templates/
          |-- appname/
              |-- first_template.html
````
1) Create a template directories to namespace the template
   1) Inside the project app directory ````appName/````, create a folder named ````templates/````
   2) Create a folder named after your app to namespace your template:
      - Example: ````appName/templates/appName/````
2) Within the namespaced template folder insert all your HTML files for your webpage.
   - Example: ````appName/templates/appName/filename.html````

## Create a View Function
To display your HTML code onto the webpage we first have to write a view function to send when the page is requested.
1) Inside the app that was created open the views.py file to device a new function ````functionName()```` that takes
the perameter, ````request````
2) In ````functionName()````, return the render function with two arguments:
   1) First argument is ````request```` 
   2) Second argument is the path to your HTML code as a string, example: ````'appName/filename.html'````
    ````
    def functionName(request):
      return render(request, 'appName/filename.html')
    ````
   ````return render()````, Rendering the template is the Django application taking the template and displaying it as 
a normal HTML page in a web browser.
3) Now the function will send our HTML code when requested, next step is to tell Django which URL to use in 
this function.
   1) Create a URLconf for the new app by creating a file named ````urls.py```` inside the app directory.
   2) Open the urls.py file and enter the following to import the necessary modules
      1) ````from django.urls import path````, imports the path module from django.urls
      2) ````from . import views````, imports the functions from views.py
4) Create a list called ````urlpatterns````, this will provide a list of patterns for Django to match URLs against.
Inside the list add a route to the function using the ``path()`` function.
   1) Note:
      1) Use dot notation whene referencing the function from views.py
      2) In the example below the first argument is an emtpy string ``""``, this will have our app appear as our 
      main page
    ````
   urlpatterns = [
       path("", views.functionName)
   ]
   ````
5) Inside the DjangoProject/DjangoProgect/urls.py file, import the ``include`` module from ``django.urls``. This will allow the 
project’s URLconfig for the URLs to be picked up by the Django project.
   1) Line 17 of the urls.py file should look like:
   ````from django.urls import path, include````
6) Inside the project URLconfig, DjangoProject/DjangoProgect/urls.py, include the appName URLs, using the 
urlpatterns list. Example:
    ````
    urlpatterns = [
      # ... other paths
      path("", include("appName.urls"))
    ]
    ````
