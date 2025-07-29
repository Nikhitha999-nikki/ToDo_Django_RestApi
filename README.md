# ToDo_Django_RestApi
Django To-Do API
A minimal and efficient To-Do list management system built with Django and Django REST Framework.
This project provides an API to create tasks and a backend admin interface for task management.

🔍 Overview


📌 Create To-Do using a RESTful API (POST only)

📂 Manage tasks in Django’s built-in Admin panel

🌐 Browsable API interface for interactive testing

✅ Task fields: Title, Description, Date, Completed

🔐 Secure admin control with login authentication



🧩 Project Structure 
📁 django-todo-api

 ┣ 📁 mainApp
 
 ┣ 📁 screenshots
 
 ┃ ┣ create_todo.png
 
 ┃ ┗ admin_dashboard.png
 
 ┣ 📄 manage.py
 
 ┣ 📄 requirements.txt



API-end points
http://localhost:8000/api/
Here you will see the list of all the tasks you have created. Read the task here.


![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/3c24522786f2c2cd1d9d3e6e7ae6f4135f3eef2c/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_12_25%20AM.png)

To update the existing task, you can update it using their id. For example, if we want to update our first task and the id of the first task is 1.then the API-end point will be.
http://localhost:8000/api/1/


![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/3c24522786f2c2cd1d9d3e6e7ae6f4135f3eef2c/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_19_49%20AM.png)


📋 Admin Panel (/admin/)
View, edit, or delete tasks
Intuitive dashboard for quick task management

 
![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/4ca86750efa70a4463acc717f1db7dc63eef234a/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_15_00%20AM.png)



To create a post, the API-end point is: http://localhost:8000/api/create
![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/3c24522786f2c2cd1d9d3e6e7ae6f4135f3eef2c/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_20_17%20AM.png)



Now the last part is to Delete the task. let’s suppose you have to delete the first task. So the API-end point would be: http://localhost:8000/api/delete/1
![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/3c24522786f2c2cd1d9d3e6e7ae6f4135f3eef2c/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_22_29%20AM.png)



We have now completed the CRUD operation in the TO-DO Rest API using Django Rest Framework.
![Image Alt](https://github.com/Nikhitha999-nikki/ToDo_Django_RestApi/blob/4ca86750efa70a4463acc717f1db7dc63eef234a/List%20To%20Do%20%E2%80%93%20Django%20REST%20framework%20-%20Google%20Chrome%207_26_2025%209_21_23%20AM.png)



🌐 API Behavior


  Endpoint	    Method	         Action	     Description
  
/api/create/	   POST	   Create Task	       Adds a new To-Do item

/api/create/	   GET	  ❌ Not Allowed	     Returns 405 Method Not Allowed

/admin/	         GET	   View Admin Panel	   Manage To-Dos through admin backend



🛠 Tech Stack


Framework: Django


API: Django REST Framework


Database: SQLite


Interface:  Django Admin


Thank you.
