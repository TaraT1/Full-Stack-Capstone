## Where's My Stuff?
A place to record the location of stuff.

This app is written in Python with Flask and SQLAlchemy as part of Udacity's Full Stack Web Developer Nanodegree program. It uses a PostgreSQL database.

Deployed at https://forstuff.herokuapp.com/

Heroku git https://git.heroku.com/forstuff.git

Github: https://github.com/TaraT1/Full-Stack-Capstone


#### Connect Postgres Database
After the first install and each time you restart your machine you will have to also restart the postgres service, or else you will get an operational error. (Is the server running?)
	1. To start the service, type ```sudo service postgresql start```
	2. To connect to postgres, type ```sudo -u postgres psql```
	
You should get a prompt asking for your password. If this doesn't work, then you can try the second option listed below.
	1. Switch users to postgres by typing su - postgres
	2. Type psql.
When this is successful you will see the command line change to look like this postgres=#

Connect to stuff database with
``` \c stuff ```

Other postgres commands are: 
\c <db_name> - connects to <db_name>
\l - lists tables
\dt - list of relations
\d <table/relation_name> - lists columns

Stop the PostgreSQL server:
```sudo service postgresql stop```

#### Installation of Development Environment
python 3.7

* `python3 -m venv env` set the virtual environment for Pyhton 
* `source venv/bin/activate` activate the virtual environment
* `python -m pip install -r requirements.txt` to install dependencies. All required packages are included in the requirements file. 
* `deactivate` - de-activates the virtual environment


#### Invoke app from Linux CLI:
```python 
export FLASK_APP=app.py
export FLASK_ENV=development
flask run
```
#### Invoke app from Windows CLI:
```python 
set FLASK_APP=app.py
set FLASK_ENV=development
flask run
```
### Authentication
jwt URL: https://fs-cap.us.auth0.com/authorize?audience=stuff&response_type=token&client_id=MihahCAfPHgMqflvzrtWBBULAi40i9eb&redirect_uri=http://localhost:8080/login

#### Owner Role
Owner has all permissions.

##### Permissions
post:locations		post:books
get:locations		get:books
patch:locations		patch:books
delete:locations	delete:locations

##### Login details:
email: owner@stuff.com
password: passwoid123!

#### User Role
The user role has retrieve permission only

##### Permissions
get:locations		get:books

##### Login details:
email: user@stuff.com
password: passwoid123!

## API documentation 
### CURL COMMANDS
#### Create
#####Location

```Heroku curl
curl -d '{
	"name": "curltst1Na",
	"type": "curltst1Ty",
	"book": "curltstBo"
}' -H "Content-Type: application/json" -X POST https://forstuff.herokuapp.com/locations/add
```

```Local curl
curl -d '{
	"name": "curltst1Na",
	"type": "curltst1Ty",
	"book": "curltstBo"
}'-H "Content-Type: application/json" 
-X POST http://127.0.0.1:5000/locations/add

#####Book
```Heroku curl
curl -d '{
	"title": "Ctitle", 
	"author": "Cauthor", 
	"form": "Cform"
	}' -H "Content-Type: application/json" 
	-X POST https://forstuff.herokuapp.com/books/add
```

```Local curl
curl -d '{
	"title": "Ctitle", 
	"author": "Cauthor", 
	"form": "Cform"
	}' -H "Content-Type: application/json" 
	-X POST http://127.0.0.1:5000/books/add
```
#### Retrieve
```Heroku curl
curl -X GET 'https://forstuff.herokuapp.com/locations'
```

```Local curl
curl -X GET 'http://127.0.0.1:5000/locations'
```

#### Patch
```Heroku curl
curl https://forstuff.herokuapp.com/books/1 -X PATCH -H "Content-Type: application/json" -d '{"title": "PC2title"}'
```
```Local curl
curl http://127.0.0.1:5000/books/1 -X PATCH -H "Content-Type: application/json" -d '{"title": "PC2title"}' 
```

#### Delete
```Heroku curl
curl -X DELETE https://forstuff.herokuapp.com/books/5
-H "Accept: aplication/json"
```
```Local curl
curl -X DELETE http://127.0.0.1:5000/books/5
-H "Accept: aplication/json"
```