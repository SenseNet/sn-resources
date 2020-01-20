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
* Freeze *develop* branch (do not merge any more pr to develop)
* Create a release branch with [git flow](https://danielkummer.github.io/git-flow-cheatsheet/#release)
* Increase the root package.json version to match with [semver](https://docs.npmjs.com/about-semantic-versioning)
* Run `yarn lerna version --no-git-tag-version --include-merged-tags`
  * bump packages version
* Open pull request to *master* branch
* Do some testing (run unit and e2e tests)
* Audit the netlify build with [Lighthouse](https://developers.google.com/web/tools/lighthouse#devtools), check for regressions
* Check [relativeCI](https://app.relative-ci.com/projects/SpRCK0ViJsBVzSUtpFtk) for bunde size changes
* Fix showstopper bugs in *release* branch
* Write changelog/package release and aggregated changelog and newsletter, blog, social
  * Create a changelog in [sensenet.github.io](https://github.com/SenseNet/sensenet.github.io) under _updates

On Wednesday:
* Do the branching
  * Update your master and develop branches (`git checkout develop && git pull` and `git checkout master && git pull`)
  * When everything is green on your pr, checkout the release branch on your computer if not checked out previously
  * run `git flow release finish *RELEASE*` or finish it in gui with [SourceTree](https://www.sourcetreeapp.com/) // where RELEASE is the name of the release branch eg release/2019.6.0 would be 2019.6.0 
    This will close the pull request on GitHub.
  * Push develop and master to origin with the git tag `// git push origin --tags`
* Publish to npm
  * `git checkout master`
  * `npm login`
  * `yarn` // To install dependencies
  * `yarn clean:packages` // This will remove all dist folders from the packages
  * `yarn build`
  * `yarn test` // Sanity check
  * `yarn lerna publish from-package` // Lerna will publish all the packages that aren't in the registry yet
* Edit the release tag in GitHub and paste the changelog from [sensenet.github.io](https://github.com/SenseNet/sensenet.github.io) 
* Have a good one! 🍺 You have just published a new release. 🌟

Post-release tasks
* Update dependencies in the [sn-client](https://github.com/SenseNet/sn-client) monorepo
  * create a new branch from develop
  * `yarn upgrade-interactive --latest`
  * `delete yarn.lock`
  * `yarn` // To re-create yarn.lock

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

