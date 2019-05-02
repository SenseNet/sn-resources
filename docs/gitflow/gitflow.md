# SN Gitflows

Branches
* *master*: permanent branch for production environments
* *develop*: permanent branch for aggregating feature branches
* *feature*: temporary branch for features and bugfixes
* *staging*: temporary branch for each release, used for creating near production QA environment with released backend
* *hotfix*: temporary branch for urgent and high importance fixes

## Feature flow
* Start with a well defined issue
* Create a *feature* branch from *develop* branch
* Open a pull request (enables you to have a look on netlify, etc) to *develop* branch
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
* yarn clean:packages
* yarn build
* yarn jest/yarn test
* Lerna publish
* Merge *staging* into *master*
* Merge *staging* into *develop*
* Remove *staging* branch
* Related issues --> Close

## Hotfix flow
* Create *hotfix* branch from *master* branch
* Open a pull request to *master* branch
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
* Frontend: https://dms.demo.sensenet.com - *master* - built daily

Staging
* Backend: https://dmsservice.demo.sensenet.com - *master* - built daily
* Frontend: Dynamic URL from the release branch's PR (Netlify)

Develop
* Backend: https://devservice.demo.sensenet.com/ - *develop* - built daily and on change
* Frontend: https://sn-dms-demo-dev.netlify.com - *develop* - built daily

