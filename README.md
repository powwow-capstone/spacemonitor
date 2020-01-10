# powwowEnergyCapstone
## Cloning this repo:
`git clone --recurse-submodules https://github.com/powwow-capstone/spacemonitor.git`


## Committing to Github:
**Make sure that your submodule branches and root repo branch are on the intended branches for commits**

If typing `git status` returns one of the submodule directories as modified or untracked. 

### Example Commit
For example, I've updated a file in the `frontend` submodule directory I want to push my updates to BOTH the superproject repo and the submodule repo. Running `git status` in the root directory produces the following output:
```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  (commit or discard the untracked or modified content in submodules)
	modified:   frontend (modified content)

no changes added to commit (use "git add" and/or "git commit -a")
```

1. Change to the modified/untracked directory.
`$ cd frontend`

2. Add and commit your changes to the submodule's own repository.
```
$ git add src/components/SimpleMap.js
$ git commit -m "Updated map"
```

3. Push your changes.
`git push origin <branch>`

4. Return to the root directory. Note that the frontend directory shows "(new commits)" instead of "(modified)" now
```
$ cd ..
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   frontend (new commits)

no changes added to commit (use "git add" and/or "git commit -a")
```

5. Add and commit the changes to the submodule.
```
$ git add frontend
git commit -m "Updated SimpleMap.js in frontend"
git push origin <branch>
```

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
