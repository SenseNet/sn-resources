# Single Page Application requirements

## Version control

 - Create a repository on GitHub for the package with a readme.
 - Set the *.gitignore* to *Node*
 - Set the publicity and the license according to your needs
 
## Project settings and scaffolding, IDE
 - Use [Visual Studio Code](https://code.visualstudio.com/) for SPA development
 - Creating the project structure with [create-react-app-typescript](https://github.com/wmonk/create-react-app-typescript) is **highly recommended** with *ejecting*
     - You should turn off *uglify* for production builds
 - Use Webpack for bundling and for development server
 - Write your code in [TypeScript](https://www.typescriptlang.org/) and your components in *tsx*
 - Set the tsconfig type checking rules as strict as possible. You can take [our](https://github.com/SenseNet/sn-dms-demo/blob/master/tsconfig.json) tsconfig as a starting point
 - Use *tslint* for code linting. You can take [our](https://github.com/SenseNet/sn-dms-demo/blob/master/tslint.json) config as a starting point
 - Write tests in mocha / jest.
 
## Usage with Sensenet
 - Always use the latest released version of the [@sensenet](https://www.npmjs.com/search?q=%40sensenet) scoped packages from NPM
    - Use [@sensenet/redux](https://www.npmjs.com/package/@sensenet/redux) for React/Redux 

## CI Tools
 - Set up [Travis](https://travis-ci.org/) for CI builds. you can take our [config](https://github.com/SenseNet/sn-client-core/blob/master/.travis.yml) as a starting point
    - Always build your project on the latest **LTS and Current** version of node.js
    - The build process should:
        - Run lint on the full project
        - Build the project
        - Run the tests
        - Report the code coverage to CodeCov
 - Set up [Codecov](https://codecov.io/) for monitoring test coverage
 - Enable [GreenKeeper](https://greenkeeper.io/) to monitor your dependencies
 - Enable **license/cla** if required
 
## Commits, branching and pull requests
 - Generate your commits with [Commitizen](https://github.com/commitizen/cz-cli) command line utility
 - Use semantic versioning
 - Always use the GIT Flow and pull requests
 - Monitor your pull requests with CI tools. Enable status checks for:
     - codecov/patch
     - codecov/project
     - continuous-integration/travis-ci
     - license/cla (if required)
     
## References
-  [Introduction to How to Write an Open Source JavaScript Library](https://egghead.io/lessons/javascript-introduction-to-how-to-write-an-open-source-javascript-library)
