---
title: "Express JS"
date: 2020-11-01T14:00:00+03:00
draft: true
toc: false
images:
tags:
  - "express-js"
  - "rest-api"
  - "api"
---

It's Time to write our first REST API. But first we need to brush through the basics.

### What's an API?

Put simply, an API is a server side application which has the ability to recieve HTTP requests (GET,POST,PUT,UPDATE) and provide a response. API's can send back responses as JSON or XML.

### How about REST?

Representational State Transfer (REST) is a design pattern (or style) for building APIs. Some of the principles which need to be met for an API to be reffered to as a REST API are:

- **Client-Server** - The user interface should be separated from data storage concerns

- **Stateless** - Each request to the API must contain all the information required to process the request. (Session state is kept by the client)


### Introducing Express JS

Express is a framework used to build API's using Node JS. In order to use Express we need to install it as a dependancy using NPM.

First let's create a new directory for our API.

```bash
mkdir rest-api

cd rest-api
```

We then need to initialize our Node JS project using the command ```npm init```. Once we are done with that we can now install Express as a dependancy.

```bash
npm install express
```
Once the installation is complete, you will notice a new directory `node_modules` and a new file `package.json`

#### Node Modules

This directory contains all the dependancies our project requires. You might be wondering why it has so many other folders inside it yet we only installed one `Express JS`.

Node_modules stores our projects dependancies and the dependancies of our dependancies. So when we installed Express as a dependancy, it went ahead and installed Express' dependancies too.

#### Package.json

This describes our project (information we provided when we ran the command `npm init`). It also defines our project's dependancies. 


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
First define a constant variable `express` and call the function `require()`. We use this function to import dependancies we have installed in our project. Since we are using Express to build our API, we first need to import it into our project

```js
const app = express();
```

We call the function `express()` and assign the return value to the variable `app`. The `express()` function creates our Express application (API) and we store the application on the variable `app`.

```js
app.listen(3000,function(){
  console.log("Listening for requests on port 3000")
})
```

We instruct our API (stored in the variable `app`) to listen for requests on port 3000. The port number can be any port which isn't being already used. List of [available ports](https://www.browserstack.com/question/664)

The `listen` function has 2 arguments, a port to listen to and a callback function. So once our API has established a connection to port 3000, it will print `Listening for requests on port 3000` on the console.

On the next article we will dive into route handling using Express. 

Cheers.