## Flask Tutorial
Flask is a lightweight web framework of Python. It provides the user with libraries modules and tools to help build Web-Applications such as blog or wiki. This tutorial aims to install and use Flask.
#### Getting Started
In order to complete this tutorial, you need to have [Python](https://www.python.org/downloads/) installed on the your system. Then, we will create a virtual environment with `pipenv` to work on Flask on the isolated environment.
#### Operating System
This tutorial is based on Windows 10 Pro Operating System
#### Virtual Environment Setup
If haven't been done, install pipenv. Open a terminal on Windows, such as powershell, cmd. Then use the command below to install `pipenv`
```
pip install pipenv
```
On your windows system, create a new Flask project folder
```
mkdir Flask-Tutorial-new
```
Navigate into the Flask project folder that just created
```
cd Flask-Tutorial-new
```
Create a new virtual environment inside this folder
```
pipenv install --python 3.8.1
```
This will create the virtual environment folder in `C:\Users\[username]\.virtualenvs`

![2020-03-18 00_59_35- virtualenvs](https://user-images.githubusercontent.com/57285863/76912322-c31b4380-68b3-11ea-83d9-747dcbd7e13a.png)
Activate the project's virtualenv, run
```
pipenv shell
```
Install Flask
```
pipenv install flask flask-sqlalchemy
```
If you want to turn this into Git repository, this is a good place to run
```
git init
```
It will be the root of the project, and if you want to export the codebase to a different machine, it will help to have all neccessary setup files here.
Then, we will turn a codebase to installable Python Distribution. At the project's root, create `setup.py` and a directory call `todo` to keep the source code.

Here is how `setup.py` should look like:
~~~~{.python}
from setuptools import setup, find_packages

requires = [
    'flask',
    'flask-sqlalchemy',
    'psycopg2',
]

setup(
    name='flask_todo',
    version='0.0',
    description='A To-Do List built with Flask',
    author='Shutima',
    author_email='<Your actual e-mail address here>',
    keywords='web flask',
    packages=find_packages(),
    include_package_data=True,
    install_requires=requires
)
~~~~
From the above code, you can see that whenever you want to install or deploy the project, you will have all the neccessary packages in `requires` list. Everything you need to set up and install the package is also in `site-packages`.
[How to write the Python setup script](https://docs.python.org/3/distutils/setupscript.html)
Navigate into the `todo` folder created from above step. In here, create a blank `__init__.py` file and `app.py` file.
![2020-03-18 01_21_45-todo](https://user-images.githubusercontent.com/57285863/76913300-e3003680-68b6-11ea-85ca-2684f9918d25.png)
- The `__init__.py` file allows you to import from `todo` folder as if it were an installed package.
- The `app.py` is the application root. This is the place where all the Flask stuff will go, and you will create an environment that points to that file. If you use `pipenv`, you can locate your virtual environment location with command:
```
pipenv --venv
```
![2020-03-18 01_25_36-● README md - Flask-Tutorial-1 - Visual Studio Code](https://user-images.githubusercontent.com/57285863/76913491-6ae64080-68b7-11ea-8c57-b023785a4bd2.png)

Then you can set up that environment variable in your environment's `activate` script.
![2020-03-18 01_26_44-An introduction to the Flask Python web app framework _ Opensource com](https://user-images.githubusercontent.com/57285863/76913610-c57f9c80-68b7-11ea-974e-55b3aad4287c.png)

In the `activate` script, add these lines at the bottom
```
export FLASK_APP=$VIRTUAL_ENV/../todo/app.py
export DEBUG='True'
```
Set path for Flask app:
```
 set FLASK_APP=C:\Users\spoti\Documents\DE_Projects\Flask-Tutorial-1\todo\app.py
 ```
 Once you installed Flask, the `flask` command-line script was also installed. The command below will prompt the virtual environment's Flask package to run an HTTP server using the `app` object in whatever script the `FLASK_APP` path environment is pointed to.
 Now, we will focus on `app` object. For `todo/app.py` file, this will create an `app` object. It wil act as the central configuration object for the entire application. This file allows us to set up different functionalities such as a database connection, authentication, etc.
 Here we will create the most basic Flask application as followed:
 ~~~~{.python}
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    """Print 'Hello, world!' as the response body."""
    return 'Hello, world!'
~~~~
The code below takes `_name_` of the script file. The `app.route` decorates the first `view` function. Any view must be decorated by `app.route`. For this example code, when the app is executed and accessed at `http://domainname/`, you will receive `Hello, World!` as a respond.
📌If you use PowerShell, please set up FLASK_APP environment variable as followed (as PowerShell managed environment variables differently)
```
$env:FLASK_APP="C:\[path-to-flask-project-venv]\todo\app.py"
```
Start Flask by:
```
flask run
```
The web application has started and here you can get the URI to test.
![2020-03-18 01_56_15-Windows PowerShell](https://user-images.githubusercontent.com/57285863/76914861-cadee600-68bb-11ea-9aec-081e507f53f4.png)
Accessing this URI on the web browser, you should get the output of the appliction.
![2020-03-18 01_57_54-127 0 0 1_5000](https://user-images.githubusercontent.com/57285863/76914915-e8ac4b00-68bb-11ea-9a0d-22a01b3d53e9.png)

# Work in Progress