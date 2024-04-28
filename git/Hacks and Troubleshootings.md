### Excluding unwanted files to be committed into Git repo

Its often the case some system/OS/tool/editro specific files were committed into git repositories and most of the times they do not belog to the source code. 

This procedure guides on excluding unwanted files into git: 

In this example, I took MacOs specific file [.DS_Store](https://en.wikipedia.org/wiki/.DS_Store), however it can be unwated file (e.g. .project. .settings, .vascode etc).

##### **Use case:  **.DS_Store flies are already comitted into repository in a specific directory

```
git rm --cached .DS_Store

git add .

git commit -m "Removed .DS_Store from current repository"

git push origin master 
```

#### **Use case:  **.DS_Store flies are already comitted into repository in a specific directory
