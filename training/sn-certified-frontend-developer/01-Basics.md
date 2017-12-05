# 01 - Basics

## Git - Basic concepts and operations

### Remote and Local repositories

**Remote repository:** The codebase is on a “central” server and people retrieve files from it and commit to it. (e.g. on GitHub or TFS Server)

**Local Repository:** The local repo is on your computer and has all the files and their commit history, enabling full diffs, history review, and committing when offline. 

You can create a Local repository from a remote one using by *cloning* it:
```sh
$ git clone http://username@hostname.com/giturl/gitreponame.git
```

### Commiting changes

1. Add files to staging: ```git stage filename``` or ```git stage .``` if you want to include all changes. These files will be included in the next commit.
2. Create the Commit: ```git commit -m "Commit message"```

### Push, pull
You can *pull* the changes from the remote repository with the command ```git pull```.
You can *push* your commit to a remote repository with the ```git push``` command.

### Create branch, checkout, merge

You can create a new branch with ```git branch mybranchname```. You can switch between branches with the **checkout** command like ```git checkout mybranchname```.
Your files will be *overridden* during branch checkout.

### .gitignore

If there are local files / directories that you want to be ignored, you can add them to the **.gitignore** file.

### GIT Flow
Git Flow is a recommendation how you can manage your feature, release and hotfix branches.
It has two mandatory branches:
 - master - usually the *latest released* codebase
 - develop (or development) - the latest *not released, but finished* features
#### Feature development workflow
 1. Create a new *feature branch* from develop
 1. Implement the feature in the *feature branch*
 1. Once the feature is ready, merge it back to *develop*
 1. Remove the feature branch

#### Release workflow
 1. Create a *release branch* from the latest *development branch*
 1. Commit the release related changes to the **release branch** (e.g. version changes, etc...)
 1. Merge the *release branch* to **develop** AND to **master**
 1. Remove the *release branch*

#### Hotfix workflow
 1. Create a *hotfix branch* from **master**
 1. Implement the hotfix in the **hotfix branch**
 1. Merge the hotfix branch to **develop** AND to **master**

### Pull Requests (~merge requests)
When using **Git Flow**, it is not recommended to commit directly into the *master* and the *development* branch (actually,they can be *protected branches* as well) That means that changes can be only *merged* into them.

You can use [pull requests](https://help.github.com/articles/about-pull-requests/) to achieve this.

There are many advantages:
 - Code review can be requested
 - You can *connect* pull requests to issues
 - The status can be tracked by [several CI Tools](https://community.sensenet.com/blog/2017/10/11/CI-Tools-We-Use)
 - Pull requests can check about merge conflict **before trying to merge**
 - You can *squash* pull requests into one commit

### GIT commands and their TFS equivalents
 
|TFVC	                    |Git|
|---------------------------|:--|
| Check-In	                |Commit + Push|
| Get Latest Version	    |Pull|
| ‘Map Local Path’	        |Clone|
| Shelve	                |Stash (only local though)|
| Label	                    |Tag|
| ‘Compare Local to Server’	|Fetch|
| Checkin and get Latest	|Sync|

[original article](https://wilsonmar.github.io/tfs-vs-github/)


### Useful links

[Summary about the GIT Contepts](https://www.intertech.com/Blog/introduction-to-git-concepts/)

[Download GIT client for Windows](https://git-scm.com/download/win)

[SourceTree, a Windows app for GIT Repositories and Git Flow](https://www.sourcetreeapp.com/)

[GIT cheat sheet on GitHub](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

[About Pull Requests on GitHub](https://help.github.com/articles/about-pull-requests/)

[git-flow cheat sheet](https://danielkummer.github.io/git-flow-cheatsheet/)


## Visual Studio Code