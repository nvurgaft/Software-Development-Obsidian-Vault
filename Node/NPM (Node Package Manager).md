NPM is the default build tool and package manager for Node projects. It comes with the [[Node/Installation|Installation]].

NPM is used to download dependencies for your Node projects, all dependencies are placed inside the `node_modules` directory at the project root directory.

NPM utilized the `package.json` file.  This file allows the developer to add and remove dependencies, change dependency versions, add build scripts, add project metadata, add test dependencies define proxy rule and more.

Verify NPM exists by running

```sh
npm --version
```

To create a new Project run

```sh
npm init -y
```

A new `package.json` file will be created

```json
{                                                                                     
  "name": "test",                                                                     
  "version": "1.0.0",                                                                 
  "description": "",                                                                  
  "main": "index.js",                                                                 
  "scripts": {                                                                        
    "test": "echo \"Error: no test specified\" && exit 1"                             
  },                                                                                  
  "keywords": [],                                                                     
  "author": "",                                                                       
  "license": "ISC"                                                                    
}
```

To install a new dependency, use the `install` command (or `i` for short)

```sh
npm install axios
```

You can install multiple dependencies in one command

```sh
npm install <dep_a> <dep_b> <dep_c>
```

To install development dependencies (dependencies that will not be attached to the build but will be exposed for tests and script), add the `--save-dev` argument

```sh
npm i chai --save-dev
```

NPM will install the latest stable versions of Axios and Chai, and add these dependency to `package.json`.

```json
{
  "name": "test",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "axios": "^1.13.6"
  },
  "devDependencies": {
    "chai": "^6.2.2"
  }
}
```

To run test use the `test` command

```sh
npm test
```

To run scripts (defined in the `scripts` section) use the `run` command

```sh
npm run <script_foo>
```

For help run

```sh
npm help
```