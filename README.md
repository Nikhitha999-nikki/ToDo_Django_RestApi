# ToDo_Django_RestApi
Hello Devs..!!

As backend developers, we all must know how to make an application that follows CRUD operations. CRUD basically stands for CREATE, READ, UPDATE and DELETE. You must aware of all this. If you make a rest API then your application must follow these operations. So, let’s make a Django CRUD application. We are going to make a TO-DO list that follows all the CRUD operations in Django Rest Framework. So, grab your seat and take a cup of coffee and let’s start.

Zoom image will be displayed

Set-Up and Installation
1. Make a virtual environment
2. Activate it
3. Install Django using the command: pip install django
4. Install Django Rest Framework using the command: pip install djangorestframework
If you are using Ubuntu so, you will see something like this in your terminal window
5. Now execute the command: django-admin startproject ToDo
6. Now navigate to the folder ToDo
7. Execute the command: python manage.py startapp main

   We are done with the setup and installation. Now open this project in your favorite text editor and start coding.
   Inside the main folder, create two files: serializers.py and urls.py. The tree format will look something like this.

main
| | — __init__.py
| | — __pycache__
| | | — __init__.cpython-38.pyc
| | | — admin.cpython-38.pyc
| | | — apps.cpython-38.pyc
| | | — models.cpython-38.pyc
| | | — serializers.cpython-38.pyc
| | | — urls.cpython-38.pyc
| | ` — views.cpython-38.pyc
| | — admin.py
| | — apps.py
| | — migrations
| | | — 0001_initial.py
| | | — __init__.py
| | ` — __pycache__
| | | — 0001_initial.cpython-38.pyc
| | ` — __init__.cpython-38.pyc
| | — models.py
| | — serializers.py
| | — tests.py
| | — urls.py
| ` — views.py
` — manage.py

models.py

from django.db import models
# Create your models here.
class Todo(models.Model):
    Title = models.CharField(max_length=100, blank=False)
    Description = models.TextField(blank=True)
    Date = models.DateField(blank=False)
    Completed = models.BooleanField(default=False)
def __str__(self):
        return self.Title
In the Todo App, we need a title, where we specify what to do. The description will elaborate task. Then on which date we want that task to be completed. And finally, we have a boolean field that will tell us whether the task is completed or not.

serializers.py

from rest_framework import serializers
from .models import Todo
class ToDoSerializer(serializers.ModelSerializer):
    class Meta:
        model = Todo
        fields = ('id', 'Title', 'Description', 'Date', 'Completed')
views.py

from rest_framework import generics
from .serializers import *
from .models import *
class ListTodo(generics.ListAPIView):
    queryset = Todo.objects.all()
    serializer_class = ToDoSerializer
class DetailTodo(generics.RetrieveUpdateAPIView):
    queryset = Todo.objects.all()
    serializer_class = ToDoSerializer
class CreateTodo(generics.CreateAPIView):
    queryset = Todo.objects.all()
    serializer_class = ToDoSerializer
class DeleteTodo(generics.DestroyAPIView):
    queryset = Todo.objects.all()
    serializer_class = ToDoSerializer
Here we used generic views. It was developed as a shortcut for common uses pattern. The first class of ListToDo is used to show the list of all the to-do lists. The second one is used to update the particular task. The third one is to create the task and the last one is to delete the task. In the second class, we used Retrieve and Update View. This means we first retrieve the data and then update it. Now add the following code in the urls.py file inside the main folder.

from django.urls import path
from .views import *
urlpatterns = [
    path('<int:pk>/', DetailTodo.as_view()),
    path('', ListTodo.as_view()),
    path('create', CreateTodo.as_view()),
    path('delete/<int:pk>', DeleteTodo.as_view())
]
Update the settings.py.

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
#apps
    'main',
    
    #third party apps
    'rest_framework',
]
Add the apps you create inside the INSTALLED_APPS. Also, add all the third-party apps you installed and used in this project. It is a good habit to comment on third-party apps. As it is easy to understand.

Update the urls.py file inside the ToDo folder.

from django.contrib import admin
from django.urls import path, include
urlpatterns = [
    path('admin/', admin.site.urls),
    path('api/', include('main.urls'))
]
And we are done with the code part.
Now open your command prompt or terminal window and run the server after migrations.

(project) godfather@ninza:~/Django/pr8/project/ToDo$ python manage.py makemigrations
Migrations for 'main':
  main/migrations/0001_initial.py
    - Create model Todo
(project) godfather@ninza:~/Django/pr8/project/ToDo$ python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, main, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying main.0001_initial... OK
  Applying sessions.0001_initial... OK
(project) godfather@ninza:~/Django/pr8/project/ToDo$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
May 23, 2021 - 12:13:03
Django version 3.2.3, using settings 'ToDo.settings'
Starting development server at http://127.0.0.1:8000/
API-end points
http://localhost:8000/api/
Here you will see the list of all the tasks you have created. Read the task here.

To update the existing task, you can update it using their id. For example, if we want to update our first task and the id of the first task is 1.then the API-end point will be.
http://localhost:8000/api/1/

To create a post, the API-end point is: http://localhost:8000/api/create

Now the last part is to Delete the task. let’s suppose you have to delete the first task. So the API-end point would be: http://localhost:8000/api/delete/1

We have now completed the CRUD operation in the TO-DO Rest API using Django Rest Framework.

Thank you.
