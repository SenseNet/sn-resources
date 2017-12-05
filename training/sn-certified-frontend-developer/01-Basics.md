# 01 - Basics

## Git

### Basic concepts and operations
#### Remote and Local repositories

**Remote repository:** The codebase is on a “central” server and people retrieve files from it and commit to it. (e.g. on GitHub or TFS Server)

**Local Repository:** The local repo is on your computer and has all the files and their commit history, enabling full diffs, history review, and committing when offline. 

You can create a Local repository from a remote one using by *cloning* it:
```sh
$ git clone http://username@hostname.com/giturl/gitreponame.git
```

#### Commiting changes

1. Add files to staging: ```git stage filename``` or ```git stage .```. These files will be included in the next commit.
2. 

#### Push, pull

#### 
 - Local repository concept
    - Commit
    - Push / pull
 - Branches and merging
 - Pull requests


### Differences between GIT and TFS
 
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

### GIT Flow
[git-flow cheat sheet](https://danielkummer.github.io/git-flow-cheatsheet/)

### Useful links
[Summary about the GIT Contepts](https://www.intertech.com/Blog/introduction-to-git-concepts/)
[Download GIT client for Windows](https://git-scm.com/download/win)
[SourceTree](https://www.sourcetreeapp.com/)
[GitHub GIT cheat sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)
[git-flow cheat sheet](https://danielkummer.github.io/git-flow-cheatsheet/)


## Visual Studio Code