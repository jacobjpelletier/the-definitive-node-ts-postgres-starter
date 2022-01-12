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
    "node-postgres": "^0.6.2",
     : "^5.1.1",
    "express": "^4.17.1"
  },
  "devDependencies": {
    "@types/express": "^4.17.11",
    "@types/node": "^15.0.2",
    "@types/pg": "^7.14.11",
    "@types/supertest": "^2.0.11",
    "dotenv": "^9.0.2",
    "eslint": "^8.5.0",
    "eslint-config-prettier": "^8.3.0",
    "eslint-plugin-prettier": "^4.0.0",
    "jasmine": "^4.0.1",
    "jasmine-spec-reporter": "^7.0.0",
    "jasmine-ts": "^0.4.0",
    "nodemon": "^2.0.7",
    "prettier": "^2.5.1",
    "supertest": "^6.1.6",
    "ts-node": "^9.1.1",
    "ttypescript": "^1.5.12",
    "typescript": "^4.2.4",
    "typescript-transform-paths": "^2.2.3"
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
## Docker
### What and Why
**Why**:  
In short, here we can use docker to more conveniently work with a postgres database and node app. Docker compose is used because it easily allows for defining and running multi-container projects (though can be done with a single container project as well). See official docs [here](https://docs.docker.com/compose/).     
You will need to download docker and then `npm install docker-compose`. You can learn more about how to get started with docker [here](https://www.docker.com/101-tutorial).   
- docker-compose "Builds, (re)creates, starts, and attaches to containers for a service" with additional behaviors defined [here](https://github.com/docker/docker.github.io/blob/master/compose/reference/up.md).  
- Note that docker run is not used in this project, and for the purpose of comparison [here is that](https://github.com/docker/docker.github.io/blob/master/compose/reference/up.md) documentation.  
- [here](https://stackoverflow.com/questions/33066528/should-i-use-docker-compose-up-or-run) is a good stack overflow explaining the difference.    

**What**:  
A "[Dockerfile](https://docs.docker.com/engine/reference/builder/)" is needed to build the container images.   
A "[docker-compose.yaml](https://docs.docker.com/compose/)" file is needed to start apps from the specified configuration.  
A "[.dockerignore](https://codefresh.io/docker-tutorial/not-ignore-dockerignore-2/) file to help optimize the docker process and specifies files that "won’t be packed into an archive and uploaded to the Docker server". For example, we don't need git and node_modules in our containers.

### Commands
`npm i docker-compose` 

`docker-compose up`        to turn on container

`docker-compose down`      to turn container off   

WARNING! `docker-compose rm` to delete container, not a great idea but here if you run into issues in development  

`docker exec -it <id> psql -U postgres postgres`  

where container `id` can be found by running `docker ps`  

### Configuration
Create and configure a Dockerfile in the root directory like so:
``` 
FROM node:14.16.0-slim

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

ADD https://github.com/ufoscout/docker-compose-wait/releases/download/2.8.0/wait /wait
RUN chmod +x /wait

EXPOSE 3000

CMD /wait && npm run start
```
Create and configure a .dockerignore in the root directory like so:
``` 
.git
node_modules
```
Note the two services in our docker-compose file, node and postgres. put this file in root with the other docker files.
``` 
version: "3.8"
services:
  app:
    build: .
    ports: 
      - 3000:3000
    env_file: .env
    depends_on: 
      - db
  db:
    image: postgres:10.16
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: postgres
    ports: 
      - 5432:5432
    volumes: 
      - db-data:/var/lib/postgresql/data
volumes: 
  db-data:
```
1. version specifies docker version
2. services defines our docker containers
   1. app
      1. build: `docker build` will look at Dockerfile in '.' to start to build containers
      2. ports: map host:container ports 
      3. env_file: specifies environment variables, so we can use the .env file created earlier
      4. depends_on: this service depends on db service
   2. db
      1. image: defines which version of postgres to use
      2. environment: define default postgres variables here. we can then use these defaults to login to postgres container 
      3. port: 5432:5432, 5432 is default port for postgres, so just map this container port to machine
      4. volumes: what directory will be store data in postgres - persists data in this container
   3. volume
      1. db-data: map to container, this value must be the same as db: volumes
### Documentation

__________

## Postgres
### What and Why

### Commands
`npm install -g db-migrate`

`npm install -g db-migrate-pg`

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
## Development Workflow
1. initialize and compile
   1. install dependencies
   2. run build script
   3. run dev script
2. check that docker works
   1. docker-compose up
   2. docker ps (might as well get the id now)
   3. docker-compose down
3. 

## Scripts
### Add these scripts to package.json
**Scripts are executed with `npm run <script_name>`.**  

The "build" script compiles TS to commonJS.  
1. `"build": "rm -rf dist && ttsc && cp -R ./src/db/migrations ./dist/db"`   
   - `rm -rf dist &&` remove old code found in dist folder and build from scratch
   - `tsc` to compile TS code  
The "dev" script we run during development
2. `"dev": "nodemon --watch src -e ts --exec -ts-node -r dotenv/config src/index"`
   - tells nodemon to watch for any changes in the source folder 
   - executes ts-node to read .env file apply this to run src/index.ts
The "start" script is used for production 
3. `"start": "node dist/index.js"`

