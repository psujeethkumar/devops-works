### Git Intro

* Git is distributed version control system - with remote and local repositories.
* Content tracker.
* Local repository
  * Working area - files here are unaware to git
  * Staging area - files with new changes (added, modifies, deleted lines) in several files
  * Commited files

###### Git configuration

```
git configure 
```

###### Repo initialization

```
mkdir first-repo # Created a folder foreseen as git repo

cd first-repo # navigate to that folder

git init # initialized the folder a git repo

ls -lrta # see the git specific files (.git, gitignore etc.)

git status # Displays the satatus of the repository
```

###### Add and comitting files

```
touch first-file.txt

echo "This is the first file committing into git local repossitory" >> first-file.txt

git status # Displays the first-file.txt is created and it is still in working area.

git add . # Adds the modified/new files into staging area, making those files eligible to commit into repository.

git commit -m "First commit into local repository" # Commits the file into local repo & commit messge is by dafault mandatory in git.
```
