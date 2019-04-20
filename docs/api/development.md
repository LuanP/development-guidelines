### API development !heading

* Follow the REST standards
    * [Resource naming guide](https://restfulapi.net/resource-naming/)
* Composition over inheritance
* Keep the environment names standardized
    * test - automated testing
    * development - local development
    * stage - mirror of the production environment (pre-production, used for performance testing, load testing, ensures environment is reliable)
    * pilot - small part of the real end users point to this environment and decreases the impact of errors
    * production - most part of the real end users