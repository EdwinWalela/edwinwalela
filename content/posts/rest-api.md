---
title: "Express JS"
date: 2020-11-20T08:00:00+03:00
draft: false
toc: false
images:
tags:
  - "express-js"
  - "rest-api"
  - "api"
---

It's time to build a REST API.

### What's an API?

An API is a server side application which has the ability to receive HTTP requests (GET,POST,PUT,UPDATE) and provide a response. API's can send back responses as JSON or XML.

### How about REST?

Representational State Transfer (REST) is a design pattern (or style) for building APIs. Some of the principles which need to be met for an API to be referred to as a *REST* API are:

- **Client-Server** - The user interface should be separated from data storage concerns

- **Stateless** - Each request to the API must contain all the information required to process the request.


### Introducing Express JS

Express is a framework used to build API's using Node JS. Since it's a 3rd Party framework, we need to install it as a dependency using NPM.

First let's create a new directory for our API.

```bash
mkdir rest-api

cd rest-api
```

We then need to initialize our Node JS project using the command ```npm init```. Once we are done with that we can now install Express as a dependency.

```bash
npm install express
```
Once the installation is complete, you will notice a new directory `node_modules` and a new file `package.json`

#### Node Modules

This directory contains all the dependencies our project requires.

Dependencies are applications or functions written by other developers which we can use in our projects. This reduces development time since instead of rewriting applications, we can install them as a dependency and reuse the functionality.

In Node JS, dependencies are also referred to as `modules` or `packages` and they are installed and managed using the Node Package Manager (NPM). 

There are lots of packages written by developers and to install a package we use the command:

```bash 
npm install [package-name]
```

You might be wondering why our `node_modules` directory has many folders inside it, yet we only installed one dependency (`Express JS`).

`node_modules` stores our projects dependencies and the dependencies of our dependencies. So when we installed Express as a dependency, it went ahead and installed Express' dependencies too.

#### Package.json

This describes our project (information we provided when we ran the command `npm init`). It also defines our project's dependencies. 

```json
{
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

The dependenies property of the `package.json` lists the dependencies of our project. In the above snippet, we can see that our project uses Express `version 4.17.1` or greater `(^)`. When we install other dependencies using `npm install [package-name]`, the package.json will be updated to indicate the new dependencies.

### Writing an API using Express

```javascript
const express = require("express");
const app = express();

app.listen(3000,function(){
  console.log("Listening for requests on port 3000")
})

app.get("/",function(request,response){
    response.send("Hello World")
})
```

Save this as `index.js`, run the command `node index.js` in the console and head over to `localhost:3000` on your web browser


### Breaking it Down

```js
const express = require("express");
```
First, we define a constant variable `express` and call the function `require()`. We use `require` to import dependencies we have installed in our project. Since we are using Express to build our API, we first need to import it into our project.

```js
const app = express();
```

We call the function `express()` and assign its return value to the variable `app`. The `express()` function creates our Express application (our API) and we store the application in the variable `app`.

```js
app.listen(3000,function(){
  console.log("Listening for requests on port 3000")
})
```

We instruct our API (stored in the variable `app`) to listen for requests on port 3000. The port number can be any port which isn't being used by other applications. List of [available ports](https://www.browserstack.com/question/664)

The `listen` function has 2 arguments, a port to listen to and a callback function. So *once* our API has established a connection to port 3000, it will print `Listening for requests on port 3000` on the console.

```javascript
app.get("/",function(request,response){
    response.send("Hello World")
})
```

Lastly, we call the `get()` method on our API. This instructs our API to *listen* for `GET` HTTP requests on our API's base URL: `http://localhost:3000/` . 

The `app.get()` function takes in 2 parameters, the first one is a route path and the second is a callback function. In our example the route path is the string `"/"`. 

Whenever our API receives a GET request on it's base URL `http://localhost:3000/`, the callback function we defined will be executed. 

### Wrap Up

Express is a framework which is used to build API's using Node. At the core of API design and development is route handling. On the next article we will dive into route design and handling using Express. 

Cheers.