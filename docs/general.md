## General guidelines !heading

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
