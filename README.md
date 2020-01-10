# powwowEnergyCapstone
## Cloning this repo:
`git clone --recurse-submodules https://github.com/powwow-capstone/space-monitor-main.git`


## Committing to Github:
**Make sure that your submodule branches and root repo branch are the intended branches**

If typing `git status` returns one of the submodule directories as modified or untracked:
```
space-monitor-main bryanwu$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  (commit or discard the untracked or modified content in submodules)
	modified:   frontend (modified content)

no changes added to commit (use "git add" and/or "git committed -a")
```
1. Change to the modified/untracked directory and commit your changes.
2. Return to root directory and `git add frontend` or `git add backend` (whichever is modified)

## NEW Instructions:

1. Install Docker. (For Windows, install docker toolbox)

2. Get the .env file and put it in the root

```
$ docker-compose up --build
```

To see on Windows:
```
192.168.99.100:5000 for backend
192.168.99.100:3000 for frontend
```

To see on Mac:
```
localhost:5000 for backend
localhost:3000 for frontend
```


### OLD INSTRUCTIONS: 
```
$ cd prod_server
$ pip3 install virtualenv
$ virtualenv venv
$ source venv/bin/activate
```
Do all of this from within the virtualenv shell:
```
$ pip3 install Flask
$ pip3 install flask_sqlalchemy
$ pip3 install flask_script
$ pip3 install flask-cors
$ pip3 install flask_migrate
$ pip3 install psycopg2-binary
$ pip3 install python-dotenv
$ export APP_SETTINGS=config.DevelopmentConfig
$ export DATABASE_URL=postgresql://localhost/db1  // DONT DO THIS STEP IF YOU WANT TO CONNECT TO THE REAL DB. Change the URL
$ cd ../
$ python3 prod_server/manage.py runserver
```

Type ```deactivate``` to exit the shell

NOTE: In order to run the server, these exports must be executed each time the virtualenv shell is activated.
```
$ export APP_SETTINGS="config.DevelopmentConfig"
$ export DATABASE_URL="postgresql://localhost/db1"
```

frontend packages: 
```
cd frontend
npm install 
```

To Start the Frontend:
Make sure you're in the frontend directory
```
npm start
```
[Link to tutorial](https://scotch.io/tutorials/build-a-to-do-application-using-django-and-react)
