### Excluding unwanted files to be committed into Git repo

Its often the case some system/OS/tool/editor specific files were committed into git repositories and most of the times they do not belog to the source code.

This procedure guides on excluding unwanted files into git: 

In this example, I took MacOs specific file [.DS_Store](https://en.wikipedia.org/wiki/.DS_Store), however it can be unwated file (e.g. .project. .settings, .vscode etc).

##### Use case: .DS_Store flies are already comitted into repository in a specific directory

```
git rm --cached .DS_Store

git add .

git commit -m "Removed .DS_Store from current repository"

git push origin master 
```

#### Use case: .DS_Store flies are already comitted into repository in a several sub directories

```
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch

git add .

git commit -m "Remove .DS_Store from everywhere"

git push origin master 
```

#### Global git configuration to exclude .DS_Store files in all repos

```
 echo .DS_Store >> ~/.gitignore_global

git config --global core.excludesfile ~/.gitignore_global 
```
