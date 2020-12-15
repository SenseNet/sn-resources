# SN Gitflows

Branches

- _master_: permanent branch for production environments
- _develop_: permanent branch for aggregating feature branches
- _feature_: temporary branch for features and bugfixes
- _staging_: temporary branch for each release, used for creating near production QA environment with released backend
- _hotfix_: temporary branch for urgent and high importance fixes

## Feature flow

- Start with a well defined issue
- Create a _feature_ branch from _develop_ branch
- Open a pull request (enables you to have a look on netlify, etc) to _develop_ branch
- Work on it
- Ask for review and testing. Related issues --> Review
- Review. Test it with the latest sensenet release (semi random netlify URL). Related issues --> Done
- Merge back to _develop_ branch (not during release flow)
- Remove _feature_ branch

## Release flow

Every 4th Wednesday

- Freeze _develop_ branch (do not merge any more pr to develop)
- Create a release branch with [git flow](https://danielkummer.github.io/git-flow-cheatsheet/#release)
- Increase the root package.json version to match with [semver](https://docs.npmjs.com/about-semantic-versioning)
- Run `yarn lerna version --no-git-tag-version --include-merged-tags`
  - bump packages version
- Open pull request to _master_ branch
- Do some testing (run unit and e2e tests)
  - unit tests will run on github automatically -> you should only check the results
  - e2e tests can be run on github and locally as well (on github start the AdminUI end-to-end tests workflow, locally you should run tests on https://e2e-service.test.sensenet.com repository)
  - check cypress code coverage on your local environment:
    ```
    Edit the cypress json file: baseUrl should be http://localhost:8080
    Run yarn snapp instrument command
    Wait for the admin ui to start
    Run yarn snapp cypress:coverage command
    ```
    Please attach the result to the description of the release PR.
- Audit the netlify build with [Lighthouse](https://developers.google.com/web/tools/lighthouse#devtools), check for regressions, compare it with previous results
  - lighthouse report should be run on the generated netlify url with https://dev.demo.sensenet.com repository. The recommended browser is chrome, it should be run in incognito window. In the settings you should also turn off the clear storage option. Please attach the result to the description of the release PR.
- Check [relativeCI](https://app.relative-ci.com/projects/SpRCK0ViJsBVzSUtpFtk) for bundle size changes, compare it with the previous. Please attach results to the description of the release PR.
- Fix showstopper bugs in _release_ branch
- Write changelog/package release and aggregated changelog and newsletter, blog, social
  - Create a changelog in [sensenet.github.io](https://github.com/SenseNet/sensenet.github.io) under \_updates (You should create your branch from master)

On Monday:

- Do the branching
  - Update your master and develop branches (`git checkout develop && git pull` and `git checkout master && git pull`)
  - When everything is green on your pr, checkout the release branch on your computer if not checked out previously
  - run `git flow release finish *RELEASE*` or finish it in gui with [SourceTree](https://www.sourcetreeapp.com/) // where RELEASE is the name of the release branch eg release/2019.6.0 would be 2019.6.0
    This will close the pull request on GitHub.
  - Push develop and master to origin with the git tag `// git push origin --tags`
- Publish to npm
  - `git checkout master`
  - `npm login`
  - `yarn` // To install dependencies
  - `yarn clean:packages` // This will remove all dist folders from the packages
  - `yarn build`
  - `yarn test` // Sanity check
  - `yarn lerna publish from-package` // Lerna will publish all the packages that aren't in the registry yet
- Edit the release tag in GitHub and paste the changelog from [sensenet.github.io](https://github.com/SenseNet/sensenet.github.io)
- Have a good one! 🍺 You have just published a new release. 🌟

Post-release tasks

- Update dependencies in the [sn-client](https://github.com/SenseNet/sn-client) monorepo
  - create a new branch from develop
  - `yarn upgrade-interactive --latest`
  - `delete yarn.lock`
  - `yarn` // To re-create yarn.lock
  - `yarn build`
  - `yarn test`

## Hotfix flow

- Create _hotfix_ branch from _master_ branch
- Open a pull request to _master_ branch
- Fix
- Ask for review and testing. Related hotfix issues --> Review
- Review and test. Related hotfix issues --> Done
- Write changelog and communicate
- Lerna publish
- Merge _hotfix_ into _master_
- Merge _hotfix_ into _develop_
- Remove _hotfix_ branch
- Related issues --> Close

# Environments

Test

- Backend: https://netcore-service.test.sensenet.com/ - _master_ branch - built daily
- Frontend: https://admin.test.sensenet.com/ - _master_ - built daily

Release/Staging

- Backend: https://netcore-service.test.sensenet.com/ - _master_ - built daily
- Frontend: Dynamic URL from the release branch's PR (Netlify)

Develop

- Backend: https://netcore-service.ev.sensenet.com/ - _develop_ - built daily and on change
- Frontend: https://admin.dev.sn.hu - _develop_ - built daily
