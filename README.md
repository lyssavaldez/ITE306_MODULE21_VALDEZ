# ITE306_MODULE21_VALDEZ
STEP 1: Installation of Flask
To install flask framework. If you have pip installed in your Python environment, please follow this step.

pip install Flask

If you don't have pip, please download the flask from: http://pypi.python.org/packages/source/F/Flask/Flask-0.10.1.tar.gz and execute the setup.py

Step 2: Create a Hello World - Web Server
First, we create a web server, create a dictionary to hold a JSON objects for a couple of employee records and then we add RESTful APIs for each supported operation. Please look at the below program, which creates a web server. Save the below program into hello.py and execute it.

from flask import Flask app = Flask(name) @app.route("/") def hello(): return "Hello World!" if name == "main": app.run()

The below line of the code creates an app object from Flask.

app = Flask(name)

app.run() starts the web server and ready to handle the request. But at this moment, it can handle only one request. It is defined in the below line of code.

@app.route("/") def hello(): return "Hello World !"

Execute the above program and you will see that you web server is ready to service you. Running on http://localhost:5000/ Now you can open your web browser and check your web server. The server is available in the URL http://localhost:5000/

STEP 3: Develop the RESTful Services
To develop the restful services for the planned objective, let's create an in-memory database in python using the dictionary data type. Please find the code snippet below: We can continue to use the hello.py and type the below code, just after the Flask app creation statement app =

Flask(name). empDB=[ { 'id':'101', 'name':'Dorry Britz', 'title':'Technical Leader' }, { 'id':'102', 'name':'Barbie Gurl', 'title':'Software Engineer' } ]

STEP 3.1: GET
In the previous section, we have created two employees in the dictionary. Now let's write a code to retrieve them using web services. As per our plan, we need two implementations one is to retrieve all the employees and another one to retrieve the specific employee with the given id.

STEP 3.1.1: GET All
@app.route('/empdb/employee/',methods=['GET']) def getAllEmp(): return jsonify({'emp':empDB})

In the above code, we have created a URI named '/empdb/employee' and also we defined the method as "GET". To service the GET call for the URI, Flask will call the function getAllEmp(). It will in turn simply call the "jsonify" method with employeeDB as the argument. The "jsonify" is a flask method, will set the data with the given JSON object which is passed as a Python dictionary and set the headers appropriately, in this case "Content-type: application/json".

STEP 3.1.2: Get Specific
Now we develop the rest service to get an employee with a given id.

@app.route('/empdb/employee/',methods=['GET']) def getEmp(empId): usr = [ emp for emp in empDB if (emp['id'] == empId) ] return jsonify({'emp':usr})

The above code will find the employee object with the given id and send the JSON object in the data.

STEP 4:
Double check the complete code, RUN hello.py and open your web browser on http://localhost:5000/ the basic web service that you have developed.

Hello.py

from flask import Flask from flask import jsonify from flask import request app = Flask(name) empDB=[ { 'id':'101', 'name':'Dorry Britz', 'title':'Technical Leader' }, { 'id':'102', 'name':'Barbie Gurl', 'title':'Software Engineer' } ]

@app.route("/") def hello(): return "Hello World!"

@app.route('/empdb/employee/',methods=['GET']) def getAllEmp(): return jsonify({'emp':empDB})

@app.route('/empdb/employee/',methods=['GET']) def getEmp(empId): usr = [ emp for emp in empDB if (emp['id'] == empId) ] return jsonify({'emp':usr})

if name == 'main': app.run()
