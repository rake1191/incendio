# steps to deploy py app in heroku

## Prerequisite

* A free [heroku account](https://signup.heroku.com/signup/dc) 
* python & git installed locally

```bash
mkdir heroku-app
cd heroku-app
pipenv install flask gunicorn
```

## Configs
create two files. and add below codes
* ProcFile
```
web: gunicorn wsgi:app
```
* runtime.txt 
```
python-3.7.5
```

ProcFile - commands in this file will be executed to start the app
runtime.txt - we are telling heroku which version of python we will be using

Foobar is a Python library for dealing with word pluralization.

## create a webApp

create a folder called "App" and enter it(mkdir app && cd app)

create a file - main.py and enter flask boiler template code.
Flask is a lightweight WSGI web application framework. It is designed to create webapps quick and easy.


```python
#main.py

from flask import Flask 
  
app = Flask(__name__) 
  
@app.route("/") #deault route
def home_view(): 
        return "<h1>Welcome to Geeks for Geeks</h1>" #we can replace this return statement with html templates
```

go to root directory of the project and create a new file - wsgi.py

```python
#wsgi.py

from app.main import app 
  
if __name__ == "__main__": 
        app.run() 
```

start the virtual environment

```
pipenv shell 
```

create a new repo in git and add all files

```
$ git init 
$ git add .
$ git commit -m "initializing"
```

## install [heroku CLI](https://cli-assets.heroku.com/heroku-x64.exe)

login into heroku and create a new app
```
heroku login
#login using browser 

##if you get error - EPERM: operation not permitted, open 'H:/_netrc'
##this means the CLI is unable to determine where to write the netrc file
## simply set your enviroment variable to a writable space
## $Env:HOMEDRIVE = "C:/Users/{username}/AppData/Local/heroku"
## run your terminal in admin mode


heroku create {app_name}
##example # heroku create incendio
```

push your code to heroku remote

```
git push heroku master
```

if everything goes well your app will be available at http://incendio.herokuapp.com/