# NODE-TS-POSTGRES DOCKER STARTER
by Jacob Pelletier

# What this Repo Contains:
1. A **basic starter template** for a node-ts-postgres project with docker and an exhaustive README explanation for each decision made
2. Adapted from https://github.com/dmngu9/node-ts-postgres to serve as project starter for Udacity Full Stack JS project https://github.com/udacity/nd0067-c2-creating-an-api-with-postgresql-and-express-project-starter
3. Services:
   1. node/express server in TS
   2. dockerized app and postgres DB 
   3. linting, formatting, and testing  

# Setup
Note that dependencies needed for development only will be saved to devDependencies woth `npm i --save-dev`
## Node
### What and Why
Make sure you have node and npm installed for this project. Node is the necessary runtime to write JS for the back-end,
which is essential in creating a full stack JS application.

**Node:**  
[Node](https://nodejs.org/en/about/) is an asynchronous event-driven JavaScript runtime which we can use to build a network application.  
**npm:**  
[npm](https://docs.npmjs.com/about-npm) is the package manager we will be using to install components for this project  
**package.json:**  
[package.json](https://docs.npmjs.com/cli/v8/configuring-npm/package-json) configures general information about the project  
**dotenv:**  
[dotenv](https://www.npmjs.com/package/dotenv) can be used to manage environment variables seperate from the code itself  
This is useful when: changing the port or IP, accessing static files, or access to the production vs development databases.

### Commands
`npm init -y`  
`npm i dotenv`  

### Configuration
Once you have installed node you can use npm to define a node project's metadata with the package.json file created by `npm init`
"package.json" in root directory
``` 
{
  "name": "node-ts-postgres",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "build": "rm -rf dist && ttsc && cp -R ./src/db/migrations ./dist/db",
    "dev": "NODE_PATH=src nodemon --watch src -e ts --exec ts-node -r dotenv/config src/index.ts",
    "start": "node dist/index.js"
  },
  "dependencies": {
    "@types/express": "^4.17.11",
    "db-migrate": "^0.11.13",
    "db-migrate-pg": "^1.2.2",
    "express": "^4.17.1",
    "pg": "^8.7.1"
  },
  "devDependencies": {
    "@types/node": "^15.0.2",
    "@types/pg": "^7.14.11",
    "dotenv": "^9.0.1",
    "nodemon": "^2.0.7",
    "ts-node": "^9.1.1",
    "ttypescript": "^1.5.12",
    "typescript": "^4.2.4",
    "typescript-transform-paths": "^2.2.3",
    "jasmine-spec-reporter": "^7.0.0",
    "jasmine-ts": "^0.4.0",
    "jasmine": "^4.0.1",    
  }
}
```  
".env" in root directory
``` 
NODE_ENV=development
PORT=3001
DB_HOST=db
DB_USER=postgres
DATABASE=postgres
DB_PASSWORD=password
DB_PORT=5432
DB_POOL_SIZE=2
DB_POOL_CLIENT_IDLE_TIMEOUT=10000
DB_POOL_CLIENT_CONNECTION_TIMEOUT=2000
WAIT_HOSTS=db:5432
```
__________
## Express
### What and Why
Where Node provides a runtime to execute javascript on the backend, [Express](https://expressjs.com/) is a framework that acts as a server framework that allows us to build web apps and APIs easily.
Express builds on the Node HTML module and allows us to handle requests and parses data with minimal configuration.  

Express is used to:  
1. set up a web server  
2. work with routes  
3. apply middleware

[more node/express documentation here](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction#introducing_express)
### Commands
`npm install express`  
`npm i --save-dev @types/express`  

### Configuration
no special config file needed here : )
__________
## Linters
### What and Why
[ESLint](https://eslint.org/) serves as a linter for our code. Linters ensure that the code is in accordance to some style guideline, and can prevent issues in code (like calling functions before calling them).
[Prettier](https://prettier.io/docs/en/) is an opinionated code formatter that enforces consistent parsing  

### Commands
`npm i --save-dev eslint` install ESlint  
`npm i --save-dev eslint-config-prettier` install ESLint Config Prettier  
`npm i --save-dev eslint-plugin-prettier` install ESLint Prettier Plugin  
`npm i --save-dev prettier` install prettier  

### Configuration
place this .prettierrc in root directory with the following JSON
``` 
{
  "trailingComma": "es5",
  "tabWidth": 4,
  "semi": false,
  "singleQuote": true
}
```
place this .eslintrc.js in root directory
``` 
module.exports = {
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended"
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaVersion": 13,
        "sourceType": "module"
    },
    "plugins": [
        "@typescript-eslint"
    ],
    "rules": {
    }
};
```
__________
## Extras
### What and Why
[nodemon](https://www.npmjs.com/package/nodemon) helps in development by automatically restarting the node server whenever changes are made
### Commands
`npm i nodemon`

### Configuration
no special config file needed here : )
__________
## TypeScript
### What and Why
Typescript layers on top of Javascript to add typing.  
Why do people use TS?
1. TypeScript is a way to **reduce developer error** efficiently
2. Typing is familiar to developers who have worked with strictly typed languages like Java, C#, and C++
3. TypeScript is easy to learn
4. Used in popular front-end frameworks including Angular, React and Vue
5. Supported by all major IDEs and code editors including Visual Studio Code, Sublime and Atom

[TS documentation](https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html)  

### Commands
`npm i --save-dev typescript`  
`npm i --save-dev ts-node`  
`npm i --save-dev @types/node`  
`npx tsc --init` adds the default TS config file  

### Configuration
Configure tsconfig.json like this:
``` 
{
  "compilerOptions": {
    /* Visit https://aka.ms/tsconfig.json to read more about this file */

    /* Projects */
    
    /* Language and Environment */
    "target": "es5",                                  /* Set the JavaScript language version for emitted JavaScript and include compatible library declarations. */
    "lib": ["ES6"],                                        /* Specify a set of bundled library declaration files that describe the target runtime environment. */
    "emitDecoratorMetadata": true,                    /* Emit design-type metadata for decorated declarations in source files. */

    /* Modules */
    "module": "commonjs",                                /* Specify what module code is generated. */
    "rootDir": "./src",                                  /* Specify the root folder within your source files. */
    "moduleResolution": "node",                          /* Specify module resolution strategy https://www.typescriptlang.org/docs/handbook/module-resolution.html */
    
    /* JavaScript Support */
    "allowJs": true,                                  /* Allow JavaScript files to be a part of your program. Use the `checkJS` option to get errors from these files. */

    /* Emit */
    "sourceMap": true,                                /* Create source map files for emitted JavaScript files. */
    "outDir": "./dist",                                   /* Specify an output folder for all emitted files. */

    /* Interop Constraints */
    "esModuleInterop": true,                             /* Emit additional JavaScript to ease support for importing CommonJS modules. This enables `allowSyntheticDefaultImports` for type compatibility. */
    "forceConsistentCasingInFileNames": true,            /* Ensure that casing is correct in imports. */
    "allowSyntheticDefaultImports": true,             /* Allow 'import x from y' when a module doesn't have a default export. */
    
    /* Type Checking */
    "strict": true,                                      /* Enable all strict type-checking options. */
    "noImplicitAny": true,                            /* Enable error reporting for expressions and declarations with an implied `any` type.. */
    
    /* Completeness */
    "skipLibCheck": true                                 /* Skip type checking all .d.ts files. */

    "paths": {
      "*": ["node_modules", "src/*"]
    },
    "plugins": [
      { "transform": "typescript-transform-paths", "exclude": [ "**/node_modules/**" ] }
    ]
  },
  "exclude": ["node_modules", "./dist", "spec"],
  "include": ["./src/**/*"]
}
```

__________
## Postgres
### What and Why

### Commands
`npm install -g db-migrate`
`npm install -g db-migrate-pg`

### Configuration

### Documentation

__________
## Docker
### What and Why

### Commands
`docker exec -it <id> psql -U postgres postgres` where container id can be found by running `docker ps`

### Configuration

### Documentation

__________
## Testing
### What and Why

### Commands
`npm i --save-dev @types/supertest`  
`npm i --save-dev supertest` 

### Configuration

### Documentation


__________
# Scripts and Commands
## Scripts
### Add these scripts to package.json
1. `"build": "npx tsc"` to add a build script to your package.json file  
2. 


