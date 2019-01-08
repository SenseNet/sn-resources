# SN Gitflows

Branches
* *master*: permanent branch for releases and production environments
* *develop*: permanent branch for aggregating feature developments
* *feature*: temporary branch for feature developments
* *staging*: temporary branch for creating near production QA environment with stable backend(?)
* *hotfix*: temporary branch for urgent and high importance fixes
* Q: where do bugs go?

## Feature flow
* Start with a well defined issue
* Create a *feature* branch from *develop* branch
* Open a pull request (enables you to have a look on netlify, etc)
* Work on it
* Ask for review and testing. Related issues --> Review
* Review. Test it with the latest sensenet release (semi random netlify URL). Related issues --> Done
* Merge back to *develop* branch (not during release flow)
* Remove *feature* branch

## Release flow
Every 4th Monday
* Freeze *develop* branch --> Open a *staging* branch from *develop*
* Open pull request to *develop* branch
* Testing (smoke)
* Fix showstopper bugs in *staging* branch
* Write changelog/package release and aggregated changelog and newsletter, blog, social

On Wednesday:
* Lerna publish
* Merge *staging* into *master*
* Merge *staging* into *develop*
* Remove *staging* branch
* Related issues --> Close

## Hotfix flow
* Create *hotfix* branch from *master* branch
* Open a pull request (enables you to have a look on netlify, etc)
* Fix
* Ask for review and testing. Related hotfix issues --> Review
* Review and test. Related hotfix issues --> Done
* Write changelog and communicate
* Lerna publish
* Merge *hotfix* into *master*
* Merge *hotfix* into *develop*
* Remove *hotfix* branch
* Related issues --> Close

# Environments

Release
* Backend: https://dmsservice.demo.sensenet.com - *master* branch - built daily
* Frontend: https://dms.demo.sensenet.com - *master*

Staging
* Backend: https://dmsservice.demo.sensenet.com - *master*
* Frontend: https://sn-dms-demo-*staging*.netlify.com - *staging*

Develop
* Backend: https://dmsservice.dev.sensenet.com - *develop* - build daily(?)
* Frontend: https://sn-dms-demo-dev.netlify.com - *develop* - built on change(?)

