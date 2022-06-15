---
---

# Creating a project site with Jekyll, git and github

1. [Sign up to github](#sign-up-to-github)
2. [Create the first repository](#create-the-first-repository)
3. [Push contents to the project](#push-contens-to-the-project)
4. [Create a local repo for the documentation](#create-a-local-repo-for-the-documentation)

5. [Push site content to `github`](#push-site-content-to-github)
6. Configure Jekyll to interact with github.
7. Create content
8. Push content to github repo

## Sign up to github

## Create the first repository
On github create a new repository. Do not create any files.

Obs: If you want to push an existing project, it is reommended to rename the loacal mater branch to `main`. Tha's waht is being used by github nowadays.

## Push contents to the projecto
We will create one github repository `costadm` with two branches `main` (in `proj`) and `gh-pages`(in `gh-pages`). In addition we will set the repository in a way that each branch will live in a separatye directory. Branching in either branch will not interfere with the other branch.
Create a project with the following directory structure
```
costadm
|
+-- proj
+-- gh-pages
```
`proj` is our project repo. `gh-pages` will contain our project website.
It is assumed that 'proj' is already git controlled

On local, go to the repoistory `costadm/proj` and push to github
````shell
$ cd /Users/maxi/Python/PROJECTS/costadm/proj
# set up the remote name
$ git remote add origin https://github.com/max-fic/costadm.git
# Rename the master branch to main if necessary
$ git branch -M main
# upload the contents of our local main branch
$ git push -u origin main
````
## Create a local repo for the documentation
Now we will create the gh-pages branch in `costadm/gh-pages`

We have to clone the `costadm` repo that we just pushed to `github` into the `gh-pages` directory.
```sh
$ cd /Users/maxi/Python/PROJECTS/costadm/gh-pages
$ git clone https://github.com/max-fic/costadm .
```

Now we will create a new empty branch (does not get anything from th main branch). 
 that we already have project files, we create
Make sure we create a clean branch (the --orphan option creates a branch with no predecessor)
```shell
$ git switch --orphan gh-pages
```
As we have a new branch gh-pages we can remove the main branch as it is no longer necessary (We did all this only to create the gh-pages branch in a separate directory)
```sh
$ git branch -d main
```
 If we want to content with jekyll, we have to make sure to have a `.gitignore` to avoid building the _site directory.

## Push site content to `github`
```sh
$ git commit  # commit all changes
$ git push origin gh-pages    # push to github gh-pages
```
The web page is now visible under:

`http:/max-fic.github.io/costadm`
