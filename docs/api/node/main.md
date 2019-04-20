### Node APIs !heading

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

#include "docs/api/node/koa.md"