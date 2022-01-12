# NODE-TS-POSTGRES DOCKER PROJECT
## by Jacob Pelletier
__________
# What this Repo Contains
## A basic template for a node-ts-postgres project with docker and an exhaustive README explanation for each decision
### Adapted from https://github.com/dmngu9/node-ts-postgres to serve as project starter for Udacity Full Stack JS project https://github.com/udacity/nd0067-c2-creating-an-api-with-postgresql-and-express-project-starter

# Setup
__________
## Node
### What and Why
Make sure you have node and npm installed for this project.
**Node**   
![Node](https://nodejs.org/en/about/) is an asynchronous event-driven JavaScript runtime which we can use to build a network application.

### Commands
`npm init -y`

### Configuration

### Documentation


__________
## Express
### What and Why

### Commands
`npm install express`
`npm i --save-dev @types/express`

### Configuration

### Documentation

__________
## Loggers
### What and Why

### Commands

### Configuration

### Documentation


__________
## TypeScript
### What and Why

### Commands
`npm i --save-dev typescript`  
`npm i --save-dev ts-node`  
`npm i --save-dev @types/node`  
`npx tsc --init` adds the default TS config file
### Configuration

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
## Docker
### What and Why

### Commands
`docker exec -it f82dbdb3637c psql -U postgres postgres`

### Configuration

### Documentation

__________
## Linters
### What and Why

### Commands
`npm i --save-dev eslint` install ESlint  
`npm i --save-dev eslint-config-prettier` install ESLint Config Prettier
`npm i --save-dev eslint-plugin-prettier` install ESLint Prettier Plugin
`npm i --save-dev prettier` install prettier

### Configuration
place this .prettierrc in root directory

### Documentation


__________
## Testing
### What and Why

### Commands

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
### Documentation


__________
# Scripts and Commands
## Scripts
### Add these scripts to package.json
1. `"build": "npx tsc"` to add a build script to your package.json file  
2. 


