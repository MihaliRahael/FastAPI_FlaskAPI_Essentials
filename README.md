# FAST API and FLASK ESSENTIALS

## Fast API

Fast API is a modern, fast (high performing), web framework for building APIs with python 3.6+ based on standard python type hints. It uses ASGI (Asynchronous Server Gateway Interface, a successor to WSGI, provides a standard interface between async-capable python web servers, frameworks and application. Uvicorn library ensures that when we are running the file, it has to follow the ASGI standard.

**Steps**

1.  Create an environment. Install fastapi and uvicorn using the command ,

pip install fastapi uvicorn

1.  Import uvicorn and fastapi libraries
2.  Create the object for FastAPI() (which is ‘app’ here)
3.  Define routes with our without parameters and define the respective functions inside
4.  Run the API with uvicorn by giving host address (127.0.0.1) and port number (8000).
5.  Save this file as main.py. Run the API using the command

uvicorn main:app --reload

## Flask API

Flask is a web framework written in python used for developing web application, we api machine learning applications etc. Flask is developed based on Jinja 2 template engine and WSGI concept.

WSGI (Web server gateway interface) is a standard/protocol. Usually, we host our web application in web server like Apache. Clients/public requests web server to access this web application (amazon.com). Requests are actually called as HTTP request. There is a standard /protocol exists for the communication between web server and web app, which is WSGI. Remember this web app is hosted in web server, even though it requires this wsgi for communication. There would be a functionality or callable or API in web app side which responds to web server.

Jinja 2 is a web template system, which basically dynamically integrates a web template along with a certain data source aims to render dynamic pages (gives o/p once we input something).

Eg: we have an ML application’s pickle file for classifying cat/dog. As soon as the user uploads an image, web app interacts with the pickle file or h5 file of the model and gives response. This response is coming from a specific data source, in this case data source is ML model. Data source can be a SQL or MongoDB database.

<https://github.com/krishnaik06/Flask-Web-Framework>

### Building a simple Flask application

1.  Important required libraries –
-   request : to read the Posted value (HTTP POST)
-   render_template : to render the html file inside templates folder
-   redirect , url_for - inroder to create dynamic url
1.  We basically needs two files. One is requirements.txt (contains the necessary libraries to be installed in the environment) and app.py
2.  Run ‘pip install -r requirements.txt’ in terminal
3.  Code app.py as follows.

from flask import Flask

*\# defining WSGI application*

app = Flask(**name**) *\# This will be starting point of my application where it will run*

@app.route(‘/’) *\# this is the first root. localhost/ means it should definitely go to homepage*. This is also called as decorator

def hello():

return "Hello World!"

@app.route(‘/predict’)

def predict(): *\# always remember to give different function name*

return "Prediction completed"

if \_*name*\_=="**main**":

app.run(host=”0.0.0.0”, debug=True) *\# we can also give port here*

Here Flask object we created is ‘app’ which is the WSGI standard. Whenever the app = Flask(**name**) is executed, the flask app will start its execution from if \_*name*\_=="**main**":

The decorator which binds with a function, takes two parameters, rule and options. Rule has set to “/". Whenever I go to this web page , the function hello() will get executed.

As soon as this program is executed it will start a webserver. The output will show something like “Running on <http://127.0.0.1.5000>” . In computer networks 127.0.0.1 is the local host or my current box where its IP address is 127.0.0.1 and it has a network port called 5000. On this network port it is waiting for a request from other boxes. As soon as the request come, it executes the python code and responds back. That’s how web APIs works (ie giving an IP with port number over http protocol). The above code will sent an empty request to 5000 and the computer returns “Hello world”. Host=0.0.0.0 means whatever is our local host, it will automatically get mapped to. Even if don’t give the parameters of host and port, app in run in <http://127.0.0.1.5000>.

Significance of debug=True/False. Suppose our web app is up and running and later we have made some changes in application. Inorder to reflect it in web page we need to restart the flask app. Inorder to avoid it, we can set debug=True. Then the server will automatically restarted .

### Building URL dynamically
```
| from flask import Flask,redirect,url_for                                     |
|------------------------------------------------------------------------------|
|                                                                              |
| import pandas                                                                |
| app=Flask(**name**)                                                          |
|                                                                              |
| @app.route('/')                                                              |
| def welcome():                                                               |
| return 'Welcome to my Exam results page'                                     |
|                                                                              |
| @app.route('/success/\<int:score\>')                                         |
| def success(score):                                                          |
| return "\<html\>\<body\>\<h1\>The Person is passed\</h1\>\</body\>\</html\>" |
|                                                                              |
|                                                                              |
| @app.route('/fail/\<int:score\>')                                            |
| def fail(score):                                                             |
| return "The Person has failed and the marks is "+ str(score)                 |
|                                                                              |
| \#\#\# Result checker                                                        |
| @app.route('/results/\<int:marks\>')                                         |
| def results(marks):                                                          |
| result=""                                                                    |
| if marks\<50:                                                                |
| result='fail'                                                                |
| else:                                                                        |
| result='success'                                                             |
| return redirect(url_for(result,score=marks))                                 |
|                                                                              |
|                                                                              |
| if \_*name*\_=='**main**':                                                   |
| app.run(debug=True)                                                          |
```
