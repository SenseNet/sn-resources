# 01 - Be part of the community

## Where and how to [contact](https://community.sensenet.com/contact/)

 - "How can I...?" &rarr; [StackOverflow with sensenet tag](https://stackoverflow.com/questions/ask?tags=sensenet) 
 - Submit a new issue &rarr; [GitHub](https://github.com/SenseNet) (on the corresponding repository)
 - Create a pull request &rarr; [GitHub](https://github.com/SenseNet) (on the corresponding repository)
 - Found a typo in the *[Community Site docs?](https://community.sensenet.com/docs/)* &rarr; Create a Pull Request in the [Community site's GitHub Repository](https://github.com/SenseNet/sensenet.github.io)

## Stack Overflow

### Why?
Your questions and answers can be valuable to the community. Take a [Tour](https://stackoverflow.com/tour) on StackOverflow.

### How to gain reputation
 - question is voted up: +5
 - answer is voted up: +10
 - answer is marked “accepted”: +15 (+2 to acceptor)
 - suggested edit is accepted: +2 (up to +1000 total per user)

### Loose reputation
 - your question is voted down: −2
 - your answer is voted down: −2
 - you vote down an answer: −1
 - one of your posts receives 6 spam or offensive flags: −100

### How to earn reputation quickly
- Subscribe to tags (There is a [sensenet](https://stackoverflow.com/questions/tagged/sensenet) tag)
- Ask first on stackoverflow
- Ask GOOD questions (with sample code, screenshots, etc)
- Post high quality answers (with examples, sample code, screenshots, etc)
- Try to be the first who answers
- Use upvote and comments
- Define your speciality and go Niche
- Use formatting and lists wisely
- Edit questions and answers
- Provide a good and simple code example
- Be the biggest
- Add pictures
- Use JS Bin
- Provide additional helpful info related to the question
- Help others to make their answers better, collaborate
- Provide detailed analysis of the question
- Post an answer that does what the OP wants, but the way it should be done
- Post multiple answers that are significaly different
- Once you have the priviledge to review, review a lot
- Use google effectively
- Keep your reference open
- Involve yourself to earn badges

[Original post](https://stackoverflow.com/help/whats-reputation)

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

You can create a new branch with ```git branch mybranchname```. Git providers usually handles *branch names* as paths, so you can create a virtual *folder* for features by creating a feature branch like this: ```git branch feature/my-new-awesome-feature```.

You can switch between branches with the **checkout** command like ```git checkout mybranchname```.
Your files will be *overridden* during branch checkout.

### .gitignore

If there are local files / directories that you want to be ignored, you can add them to the **.gitignore** file.
**Strong recommendation:**
 - Always ignore external packages / libraries that are managed by a package manager (e.g. NPM's *node_modules* or NuGet Packages). They should be installed by the Package Manager with ```npm install``` or ```nuget restore```.
 - Ignore build artifacts (dlls, exes, minified/bundled js, etc...). They should be created *during* the build process.
 - Try to avoid commiting large binaries.

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


## Contributing GitHub
Please always read the [contribution guide](https://github.com/SenseNet/sensenet/blob/master/CONTRIBUTING.md) before contributing.

### Creating new issues

 - Always provide a short meaningful title and description
 - State the exact version number of the project you are using
 - Provide some details on the environment (browser type in case of client-side issues, dev machine or server, stuff like that).
 - List the steps you took
 - Code samples, screenshots, log entries

### Making a change (Pull request)

 - Avoid making broad changes (e.g. a huge refactor) before talking to us; the more files you change, the harder it is to review and merge the commit.
 - Create a [fork](https://help.github.com/articles/working-with-forks/) and a *feature branch*
 - Please follow the [coding conventions](http://wiki.sensenet.com/Coding_Conventions) for .NET Projects. Respect our *tslint rules* for npm projects.
 - Test your code.
 - Run the unit tests before submitting the *pull request*. Add some tests, if possible.
 - When you are confident with your fix/feature, create a pull request. We will get notified right away 😃.
Please be patient if we do not accept the pull request immediately or ask for changes. We'll try to justify our change requests so that you know our intentions. It may speed up the process, if you allow us to modify your branch when you create the pull request.

### What are we working on?

We use the excellent [ZenHub](https://www.zenhub.com/) addon for managing GitHub issues. You can track the status on our [board](https://github.com/SenseNet/sensenet#boards)

### Related Egghead Training

[How to contribute to an open source project on GitHub](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)

## Visual Studio Code

### Why we love using VS Code?
 - Lightweight and fast
 - Great tooling support for NodeJs, NPM, Typescript and modern web technologies
 - [Frequent releases](https://code.visualstudio.com/updates/)
 - Free, open source, multiplatform

[Download](https://code.visualstudio.com/)

### Recommended addons
[TSLint](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)
[Git History(Git log)](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
[Chrome Debugger](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome)
[Git Lens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) (optional)

### Recommended Config changes

You can change your user-related settings by ```ctrl+shift+p```, **Open user settings**

```"tslint.autoFixOnSave": true``` - Auto fixable tslint errors will be fixed before saving a file.

### Optional config goodies

```"editor.minimap.enabled": true,``` - Enables a minimap on the right side

```"editor.codeLens": true,``` - Enables CodeLens

```"typescript.referencesCodeLens.enabled": true,``` - CodeLens for references

```"typescript.implementationsCodeLens.enabled": true,``` - CodeLens for interface implementations

