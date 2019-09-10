# Table of Contents

* [Guidelines for the development of API's, workers, websites and apps](#guidelines-for-the-development-of-api's,-workers,-websites-and-apps)
  * [General guidelines](#general-guidelines)
  * [Git](#git)
  * [Database guidelines](#database-guidelines)
  * [API Guidelines](#api-guidelines)
    * [API deployment](#api-deployment)
    * [API development](#api-development)
    * [Node APIs](#node-apis)
      * [Koa API](#koa-api)
      * [Hapi API](#hapi-api)
  * [Workers](#workers)
  * [Frontend development](#frontend-development)
    * [Web admins](#web-admins)
  * [Data ingestion processes](#data-ingestion-processes)
  * [Mobile development](#mobile-development)
    * [React native development](#react-native-development)


# Guidelines for the development of API's, workers, websites and apps

The guidelines of this document does not have as a function to restrict or force developers to make use of specific libraries, frameworks or programming languages.
To sum up, the reason this document was created is to aggregate knowledge and improve the base of the project structures in the companies in a way they become more closer between teams and make it possible to reduce the friction and speed up the flow when exchanging team members or when using, contributing to other team's repositories.

Clone, fork and change things to make it more suitable for your scenario.
As you find a generic guideline that may apply to a broader community, PRs are very welcome.
## General guidelines

* Apply the 12 factors in your projects - https://12factor.net/
    * Versioning your code with git
    * Keep up a repository per microservice
    * Blocking the push directly to the master branch
    * Working with forks (fork = origin, company = upstream)
    * Working with PR's and code review (suggested 2 revisions per PR)
* Check this [repository](https://github.com/github/gitignore) or https://www.gitignore.io/ to find a good .gitignore
* Configure git hooks in your project to execute lint and run tests in the pre-commit and pre-push, the ideal is that this configuration be automatic per project (to do that, check [githooks](http://githooks.com/), the lib [Autohook](https://github.com/nkantar/Autohook) and if you have a node project Husky)
* To create new releases, create tags to set the commit with the version to be released, follow the [Semantic Versioning](https://semver.org/), where the version number is composed by MAJOR.MINOR.PATCH and is incremented in the following way:
    * **MAJOR** - backward incompatible changes
    * **MINOR** - new functionalities with backward compatibility
    * **PATCH** - Fixes with backward compatibility
* Keep a **CHANGELOG** and follow the guidelines of [Keep a changelog](https://keepachangelog.com/en/1.0.0/)
    * Guiding principles
        * Changelogs are for humans, not machines.
        * There should be an entry for every single version.
        * The same types of changes should be grouped.
        * Versions and sections should be linkable.
        * The latest version comes first.
        * The release date of each version is displayed.
        * Mention whether you follow Semantic Versioning.
    * Types of changes
        * **Added** for new features.
        * **Changed** for changes in existing functionality.
        * **Deprecated** for soon-to-be removed features.
        * **Removed** for now removed features.
        * **Fixed** for any bug fixes.
        * **Security** in case of vulnerabilities.
* Configure your text editors to use space instead of tabs
* Comments are necessary, but avoid obvious or redundant comments
* Anytime it's possible, make use of a up to date generator. If you are not satisfied with the availables, create one and share with your friends
* Always create clear and good documentation in project architecture, its modules and dependencies. It reduces the time spent in understanding the project when onboarding new people.
* Doing unit tests and integration tests. Make use of TDD and BDD.
* Implement Code Coverage to measure the testing percentage of your project, e.g: https://coveralls.io/. It's also a good criteria checking the difference in the testing percentage when approving a PR
* Naming convention (Link to glossary of terms)
* Configure CI/CD pipelines with Circle CI, Jenkins, Travis, Sonar to improve the processes
* Create containers to every application with docker/docker-compose to make it easy and standardize the installation and start of the project
* Avoid multiple nesting levels, it makes the code harder to read
* Avoid that the lines have more than 80 characters to improve readability
* Metrics and logs matter! We recommend using Sentry for error logs, and prometheus for metrics, there's also newrelic and jaeger
* Always use https
* As a push notification service we recommend OneSignal 
* Know and avoid anti-patterns (Sourcemaking e Wikipedia)
    * **Accidental complexity:** Programming tasks which could be eliminated with better tools (as opposed to essential complexity inherent in the problem being solved)
    * **Action at a distance:** Unexpected interaction between widely separated parts of a system
    * **Boat anchor:** Retaining a part of a system that no longer has any use
    * **Busy waiting:** Consuming CPU while waiting for something to happen, usually by repeated checking instead of messaging
    * **Caching failure:** Forgetting to clear a cache that holds a negative result (error) after the error condition has been corrected
    * **Cargo cult programming:** Using patterns and methods without understanding why
    * **Coding by exception:** Adding new code to handle each special case as it is recognized
    * **Design pattern:** The use of patterns has itself been called an anti-pattern, a sign that a system is not employing enough abstraction
    * **Error hiding:** Catching an error message before it can be shown to the user and either showing nothing or showing a meaningless message. This anti-pattern is also named Diaper Pattern. Also can refer to erasing the Stack trace during exception handling, which can hamper debugging.
    * **Hard code:** Embedding assumptions about the environment of a system in its implementation
    * **Lasagna code:** Programs whose structure consists of too many layers of inheritance
    * **Lava flow:** Retaining undesirable (redundant or low-quality) code because removing it is too expensive or has unpredictable consequences
    * **Loop-switch sequence:** Encoding a set of sequential steps using a switch within a loop statement
    * **Magic numbers:** Including unexplained numbers in algorithms
    * **Magic strings:** Implementing presumably unlikely input scenarios, such as comparisons with very specific strings, to mask functionality.
    * **Repeating yourself:** Writing code which contains repetitive patterns and substrings over again; avoid with once and only once (abstraction principle)
    * **Shooting the messenger:** Throwing exceptions from the scope of a plugin or subscriber in response to legitimate input, especially when this causes the outer scope to fail.
    * **Soft code:** Storing business logic in configuration files rather than source code
    * **Spaghetti code:** Programs whose structure is barely comprehensible, especially because of misuse of code structures

## Git

* Commit and push frequently
* Have git hooks to run lint and unit test
* Fork the repository to start your work (branches are harder to maintain)
* Clone your forked repository (this will be your origin)
* Run `git remote set-url upstream <repository>` with the company repository clone URL
* Work in the `master` branch
* Open Pull Requests (PRs) to the `master` branch
* If you have to change your focus to work on something else, you can:
  * checkout creating a different branch in your machine
  * commit the changes
  * push to your forked repository
  * go back to the master branch and continue your work
* If you already have commited some part of your work and need to change your focus to work on something else, you can:
  * Create/checkout to a branch `git checkout -b your-branch`
  * Commit if you have something else to commit
  * Go back to the `master` branch
  * Undo the commits related to the branch you create, by running a `git reset --soft HEAD^` or `git reset --soft HEAD~2` where `2` is the number of commits. (This will undo a commit, and the second undo 2 commits)
  * If you have already sent some code to the repository, you can perform a `git push --force` on this step
* To update your master you can just run a `git pull upstream master`
* Write proper commit messages (that describe what's in that commit)
  * Write your commit message in the imperative: "Fix bug" and not "Fixed bug" or "Fixes bug."
  * Here is a [template originally written by Tim Pope](https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html):

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```
Reference: [git-scm](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)
## Database guidelines

* Database name, tables and columns using snake_case (replace spaces with underscores, e.g.: product_id)
* Take into consideration the [CAP Theorem](http://abiasforaction.net/cap-theorem/) (Consistency, Availability and Partition Tolerance) when choosing the database, always keep in mind that in system distributed through network there's failure in the delivery of messages and therefore in case of losing or delay of messages, it'll be mandatory to choose between consistency or data availabily ([Wikipedia](https://en.wikipedia.org/wiki/CAP_theorem)
## API Guidelines

### API deployment


### API development

* Follow the REST standards
    * [Resource naming guide](https://restfulapi.net/resource-naming/)
* Composition over inheritance
* Keep the environment names standardized
    * test - automated testing
    * development - local development
    * stage - mirror of the production environment (pre-production, used for performance testing, load testing, ensures environment is reliable)
    * pilot - small part of the real end users point to this environment and decreases the impact of errors
    * production - most part of the real end users
### Node APIs

* Keep at least 3 standard commands
    * npm test - It executes lint and unit tests, the ideal scenario is to display a coverage report to the developer at this moment
    * npm start - It starts the server
* We recommend the usage of the lib `dotenv` to configure environment variables in a .env file, commit this file with development information, this file will be injected and have the values changed for other environments
* Using the lib [standard](https://www.npmjs.com/package/standard) as a guide in the code style, lint e code fixer because of its proposal
* Using the lib husk to configure the hooks of precommit and prepush (those should be added to the scripts section in the package.json)
* Structure for node APIs
    * [Structure example of Node API](https://drive.google.com/file/d/1w4kt46iMJFVQAfbYbTAzr4dIIRE72dDV/view?usp=sharing) (Removing the underscores (__) of the hidden files, prefixed with a dot, e.g. __.gitkeep) - The image was taken from [generator Koa API](https://github.com/LuanP/generator-labs-koa-api)
* Using [sequelize-cli](https://www.npmjs.com/package/sequelize-cli) to manage the database migrations (Postgres, MSSQL, MySQL, MariaDB, SQLite3, Oracle and Amazon Redshift)
* Using [sequelize](https://www.npmjs.com/package/sequelize) as ORM to the databases Postgres, MySQL, SQLite3 e MSSQL.
* Avoid the usage of callbacks
* Prefer using async/await over Promise.then, Promise.catch

#### Koa API

* [Yeoman generator for Koa API](https://github.com/LuanP/generator-labs-koa-api)

#### Hapi API

* [Hapi API Structure Example](https://github.com/artth02/hapi-structure)
## Workers
## Frontend development

### Web admins

* We recommend the usage of react and creation of the project using react-scripts
* Avoid using Gulp, Grunt, Bower, Jquery
* Do not use hard coded tokens
* Do not use hard coded API URLs
* Prepare your application to use HTTPS
* Test using [Jest](https://facebook.github.io/jest/)
## Data ingestion processes
## Mobile development

* Take into consideration the usage of tools to analyse the usage of your apps, e.g. [Fabric](https://get.fabric.io/), besides serving and measuring the users engagement (time per screen, active users, usage per released version, target audience), we can analyse errors that happens in real time through the stack

### React native development
## How to contribute

* Make the change in the files inside of `docs/` (Do not edit README.md directly)
* Install the packages `npm i`
* Run `npm run compile`
* Commit, push and open a PR