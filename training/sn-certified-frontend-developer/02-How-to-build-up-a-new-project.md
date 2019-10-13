# 02 - How to build up a new project

Create your first open source js project and learn how to maintaining it on GitHub and npm

## Prerequisites

 - GitHub account
 - Installed Git
 - Installed Node.js
 - Installed VS Code

## Lesson 1 - Git and GitHub basics

### Creating a Git Repository on GitHub

 1. Navigate to [https://github.com/](https://github.com/)
 1. New Repository
 1. Fill name and description
 1. gitignore: **node**
 1. License: **gpl2**?

### Cloning via command line Git

 1. Clone or download - copy url
 1. Open **cmd** in the **parent** folder where you want to clone the Repository
 1. ```git clone <insert copied link>```
 1. ```cd <repository name>```
 1. ```code .```
 1. Close cmd


### Creating the Branches
#### Create your Development branch
 1. Open command line (CTRL+Shift+P, *Focus Terminal*)
 1. Create the *develop* branch: ```git branch develop```
 1. Checkout the *develop* branch: ```git checkout develop```
 1. Publish the *develop* branch to GitHub: ```git push --set-upstream origin develop```

#### Create  your first Feature branch for creating the readme file
 1. Create the *feature* branch: ```git branch feature/readme develop```
 1. Checkout the *feature* branch: ```git checkout feature/readme```
 1. Publish the *feature* branch to GitHub: ```git push --set-upstream origin feature/readme```

### Checkout, Change, Commit, Push
 1. Create a new file called **readme.md** in Visual Studio Code.
 1. Add some content
 1. Open the **Source Control** tab in VS Code
 1. Add the change to Staging with the **+** icon
 1. Fill the Message and click on **&check;** (commit)
 1. In the lower left corner, you can Push or Pull your changes to the remote repository with the Refresh icon
 1. Message on GitHub: **feature/readme (less than a minute ago)**

### Your first Pull request
 1. Open GitHub, navigate to your Repository page
 1. Select **Branches**
 1. Select **New pull request** near the **feature/readme** branch
 1. Change the **base** from **master** to **develop**
 1. Create the Pull Request

### Merge to Dev
 1. Open the previously created pull request
 1. Merge pull request. Now, *develop* branch will have the changes on the Readme.
 1. You can now delete the feature branch

### Lesson 2 Node.js and NPM


#### Initializing project
 1. Create and check out a new feature branch: ```git branch feature/npm-init develop``` and ```git checkout feature/npm-init```
 1. Publish the branch: ```git push --set-upstream origin feature/npm-init```
 1. Type ```npm init``` to start the initialization (we can leave all values for the default for now and YES at the end)
 1. Open **package.json** - basic structure

#### Working with packages, setup Commitizen
1. Install Commitizen with ```npm i commitizen```
1. Install Commitizen with ```npm i cz-conventional-changelog```
If you take a look on 'dependencies' in **package.json**, the *latest* 'commitizen' and 'cz-conventional-changelog' packages has been added to your package manifest.
There will be 2 changes (package.json and package-lock.json). *node_modules* is added to .gitignore by GitHub.
1. Add the following section to your package.json (commitizen-specific setting): 
   ```json
     "config": {
       "commitizen": {
         "path": "cz-conventional-changelog"
       }
     },
   ```
1. Add the following into your **scripts** section in package.json: ```"commit": "git-cz"```
1. Add the two changes for staging
1. You can run your *commit* script with ```npm run commit```
    1. Scope: **package**
    1. Short descr.: **Initialized NPM project, added Commitizen**
The following commit message will be generated: *feat(package): Initialized NPM project, added Commitizen*
1. Sync the changes
1. You can create a Pull Request on GitHub now. You can create pull requests during the feature development once the feature branch has at least a single commit. The best practice is to create the pull request as soon as possible, you can easily track your progress (mergeability, status from CI tools, etc...) there.

#### 03 - Creating a Hello Word application
 1. Create a file 'index.js' in the root of your project. This will be a simple JavaScript file that will be executed by Node.js. Add a console.log statement to see if it works.
 1. You can run your js file using Node.js: ```node ./index.js```
 1. You can execute it by creating a **start** script and call it with ```npm run start```
 1. You can create **prestart** and **poststart** scripts. These will be executed *before* and *after* the script. They will be useful if you want to *build* before start, or run a *cleanup* after a script is finished

At this point, you will have *two* changes (index.js and package.json). 
You can create two separate commit (one for package.json scripts and one for the new file). Try to make small, incremental commits with meaningful scopes and messages.
You can now finish the feature (merge the Pull request to develop) and delete the feature branch

### An example release
1. Create a *release/1.0.0* branch from *develop*: ```git branch release/1.0.0 develop``` and check it out: ```git checkout release/1.0.0```.
1. Usually, at this point you can do some release-specific changes (e.g. bumping version number). For now, let's update the Readme with the latest released version and commit it.
1. Publish the release branch
1. On GitHub, Create and finish a pull request from the **release branch** to **master**. You can use **Sqash and merge**. Remove the release branch.
1. On the console, check out the master branch and add a tag: ```git tag 1.0.0```. Push the *tags*: ```git push --tags```
1. Create and finish a pull request from **master** to **develop**. 
At this point, you have only **master** and **develop** branches, and they contains the same commits.
1. Finially, you can check *releases* and update the Release Notes.

[Single Page Application requirements](https://github.com/SenseNet/sn-resources/blob/master/docs/react-spa-requirements.md)
