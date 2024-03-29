# Introduction

- [Introduction](#introduction)
  - [Methodology](#methodology)
  - [creating the project](#creating-the-project)
  - [entry point to the application](#entry-point-to-the-application)
    - [output](#output)
    - [Test Runner](#test-runner)
    - [let's add super test](#lets-add-super-test)
  - [Development Dependencies](#development-dependencies)
    - [eslint](#eslint)
    - [config file](#config-file)
    - [prettier](#prettier)
    - [prettier config file](#prettier-config-file)
    - [nodemon installation](#nodemon-installation)
  - [setup the frontend](#setup-the-frontend)

## Methodology

![methodology](../img/1.png)
we are going to use test driven development

- first we write the test for the expected behavior
- then write the implementation to pass the test
- cleanup the code

## creating the project

```shell
npm init
```

answer the questions

```json
{
  "name": "express-ws",
  "version": "1.0.0",
  "description": "TDD with express",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "ccweerasinghe1994",
  "license": "ISC"
}
```

## entry point to the application

let's install express

```shell
npm i express
```

in our package json

```json
"dependencies": {
    "express": "^4.18.1"
  },
```

create a file called app.js

```js
const express = require('express');

const app = express();

app.listen(3000, () => {
  console.log('App is running....');
});
```

to run the app

```shell
node app.js
```

but we are not returning anything

let's add the start script to the package.json

```json
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node app.js"
  },
```

### output

```shell
App is running....
```

### Test Runner

let's add a test runner
will install jest

```shell
npm install --save-dev jest
```

let's see the package.json file

```json
 "devDependencies": {
    "jest": "^28.1.3"
  }
```

let's add a test running script

```json
 "scripts": {
    "test": "jest --watch"
  }
```

output

```shell
No tests found related to files changed since last commit
```

### let's add super test

```shell
npm install --save-dev supertest
```

## Development Dependencies

### eslint

```shell
npm install --save-dev eslint
```

or short form

```shell
npm i -D eslint
```

[eslint website](https://eslint.org/docs/latest/user-guide/getting-started)

### config file

and add the eslint config file

```json
  "eslintConfig": {
    "parserOptions": {
      "ecmaVersion": 6
    },
    "extends": [
      "eslint:recommended"
    ],
    "env": {
      "node": true,
      "es6": true,
      "jest": true
    },
    "rules": {
      "semi": [
        "error",
        "always"
      ],
      "quotes": [
        "error",
        "single"
      ]
    }
  }
```

### prettier

```shell
npm install --save-dev prettier
```

or

```shell
npm i -D prettier
```

and

```shell
npm i -D eslint-config-prettier eslint-plugin-prettier
```

### prettier config file

```json
{
  "env": {
    "node": true,
    "commonjs": true,
    "es6": true
  },
  "extends": ["eslint:recommended", "plugin:prettier/recommended"],
  "rules": {
    "eqeqeq": ["warn", "always"],
    "prettier/prettier": "warn"
  },
  "plugins": ["prettier"]
}
```

let's add prettier config file

```json
{
  "singleQuote": true,
  "printWidth": 120,
  "endOfLine": "lf"
}
```

### nodemon installation

and add nodemon ass well.

```shell
npm install --save-dev nodemon
```

and add it to the package.json

```json
   "start": "nodemon app.js",
```

now when we change the app it will restart automatically.

## setup the frontend

go to the folder where the app is created
and run this

```shell
 npx http-server -c-1 -p 8080 -P http://localhost:3000
```

flags

```-c-1 no cashing the static files
-p 8080 is for the running port
-P http://localhost:3000 request to go to
```
