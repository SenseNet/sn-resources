# Backend development requirements

## Version control

- Create a repository on [GitHub](https://github.com) or on a private git server.
   - Choose the Visual Studio *.gitignore* template.
   - Create a *readme.md* file.
   - Set the license according to your needs.
 
## Dev framework
- For a frontend-centric solution see [this article](react-spa-requirements.md).
- For ASP.NET development use **MVC** and **Web API**
> **Do not** use WebForms and old portal pages/portlets for new projects.

## Tests
- Write **unit tests** for the business logic.
- Write **integration tests** that require a repository using the [SenseNet.Tests](https://www.nuget.org/packages/SenseNet.Tests/) NuGet package.

## Infrastructure

### Builds
- Create a build for executing your tests. TFS is capable of pulling source files from public or private repositories as well.
- Create a build for installing a test site on test servers. 
   - Test sites should always be rebuilt from scratch automatically.

### Backup
- Always **stop the site** before copying the Lucene **index folder**, otherwise you may end up with an incomplete file structure.
- In a distributed environment (when there are multiple web servers with local Lucene indexes) backup the **index first**, then the database.

> In a live environment there should always be **at least two app servers** to be able to backup the local Lucene index without stopping all sites.

## Upgrade
- Always use SnAdmin packages to upgrade the application and the repository.
- For simple import/export or other common scenarios you may use the built-in [SnAdmin tools](https://community.sensenet.com/docs/snadmin-tools/) instead of creating packages manually.

> **Do not** modify the official sensenet libraries or repository parts manually - except if you forked the source code or need to debug the core libraries.