# powwowEnergyCapstone
## Cloning this repo:
> **IMPORTANT**
```
git clone --recurse-submodules https://github.com/powwow-capstone/spacemonitor.git
```

## Information about the project repository structure
The project root directory currently has 3 main directories: `backend` (submodule), `frontend` (submodule), and `data_analysis`
Submodules: https://git-scm.com/book/en/v2/Git-Tools-Submodules

> Each of the `backend` and `frontend` directories are Github repositories (I'll call them subrepos) and are linked to our working repository as submodules. In order to commit changes in both the superproject repository and the corrpesonding Github repository, we need to commit changes to both the subrepos and the superproject repository. See more about commits in the "Committing to Github" section.

> The `data_analysis` directory is a regular directory.


## Switching between the staging and production environments (i.e. staging branch and master branch respectively)
The `staging` and `prod` files are quick and dirty bash scripts for switch between the staging and production development environments respectively.

Make the files executable by running the following in the project root directory:
```
$ chmod u+x prod
$ chmod u+x staging
```

For switching to the production environment
```
$ ./prod
```

For switching to the production environment
```
$ ./staging
```

## Committing to Github:
> **Make sure that your submodule branches and root repo branch are on the intended branches for commits**


### Example Commit
For example, I've updated a file in the `frontend` submodule directory I want to push my updates to BOTH the superproject repo and the submodule repo. Running `git status` in the project root directory produces the following output:
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
```
$ cd frontend
```

2. Add and commit your changes to the submodule's own repository.
```
$ git add src/components/SimpleMap.js
$ git commit -m "Updated map"
```

3. Push your changes.
```
git push origin <branch>
```

4. Return to the project root directory. Note that the frontend directory shows "(new commits)" instead of "(modified)" now
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

## Running with Docker

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
