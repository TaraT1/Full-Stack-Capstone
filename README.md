## Where's My Stuff?
A place to record the location of stuff

This app is written in Python with Flask and SQLAlchemy as part of Udacity's Full Stack Web Developer Nanodegree program. It uses a PostgreSQL database.

Where the other projects had starter code with specific aspects of development to address, this project is self-generated.

### Backend
* Connect to postgres database
* activate virtual environment
* invoke flask app

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


#### Invoke app from CLI:
```python 
export FLASK_APP=app.py
export FLASK_ENV=development
flask run
```

### API documentation
#### CURL 
##### Retrieve
curl -X GET 'http://127.0.0.1:5000/locations'

##### Create
curl -d '{
	"name": "curltst1n",
	"type": "curltst1t",
	"book": "curltstb"
}'-H "Content-Type: application/json" 
-X POST http://127.0.0.1:5000/locations/add
b4 -X: -H "Content-Type: application/json"