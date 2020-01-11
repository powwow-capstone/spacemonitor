# PLEASE READ ME

## Cloning this repo:
> **IMPORTANT**
```
git clone --recurse-submodules https://github.com/powwow-capstone/spacemonitor.git
```

## Information about the project repository structure
Very good reference for working with submodules: https://git-scm.com/book/en/v2/Git-Tools-Submodules

The project root directory currently has 3 main directories: `backend` (submodule), `frontend` (submodule), and `data_analysis`.

From [Atlassian's tutorial](https://www.atlassian.com/git/tutorials/git-submodule) on Git submodules:
> Git submodules allow you to keep a git repository as a subdirectory of another git repository. Git submodules are simply a reference to another repository at a particular snapshot in time. Git submodules enable a Git repository  to incorporate and track version history of external code.

* As noted above, each of the `backend` and `frontend` directories are submodules and are linked to our working repository as submodules. In order to commit changes in both the superproject repository and the corrpesonding Github repository, we need to commit changes to both the subrepos and the superproject repository. See more about commits in the "Committing to Github" section.

* The `data_analysis` directory is a regular directory.

Additionally, both the `frontend` and `backend` repositories each have a `staging` branch. Every push to the `master` branch of the `frontend` and `backend` repositories will be automatically deployed to the production instance of our Heroku web app. Every push to the `staging` branch of these repositories will be automatically deployed to staging (testing) instance of our Heroku web app.

Production: http://space-monitor.herokuapp.com

Staging: http://space-monitor-staging.herokuapp.com

## Switching between the staging and production environments 

The `staging` and `prod` files are quick and dirty bash scripts for switching between the staging (staging branches) and production (master branches) development environments respectively across both submodules and the superproject repository.

** Note that these scripts both call `git submodule update --remote --merge` and will merge with the remote superproject branch for the branch that each submodule is on **

Make the files executable by running the following in the project root directory:
```
$ chmod u+x prod
$ chmod u+x staging
```

For switching to the production environment:
```
$ ./prod
```

For switching to the production environment:
```
$ ./staging
```

## Pulling the latest changes from Github
Run this to enable `git submodule update --init` whenever `git pull` is called:
```
git config --global submodule.recurse true
```

## Committing and pushing submodule changes to Github:
> **Make sure that your submodule branches and root repo branch are on the intended branches for commits**


### Example
As an example, I've updated a file in the `frontend` submodule directory and I want to push my updates to BOTH the superproject repo and the corresponding submodule repo. Running `git status` in the project root directory produces the following output:
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

#### Method 1
```
git push --recurse-submodules=on-demand
```
From the [git-scm](https://git-scm.com/book/en/v2/Git-Tools-Submodules) tutorial:
> [The "on-demand" option will] go into each submodule and manually push to the remotes to make sure they’re externally available and then try this push again.


#### Method 2
```
git push --recurse-submodules=check
```
From the [git-scm](https://git-scm.com/book/en/v2/Git-Tools-Submodules) tutorial:
> The “check” option will make push simply fail if any of the committed submodule changes haven’t been pushed.

#### Method 3
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
$ git push origin <branch>
```

4. Return to the project root directory and run `git status`. Note that the frontend directory shows "(new commits)" instead of "(modified)" now
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
$ git commit -m "Updated SimpleMap.js in frontend"
$ git push origin <branch>
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
