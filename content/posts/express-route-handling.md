---
title: "Route Handling"
date: 2020-11-01T16:00:00+03:00
draft: true
toc: false
images:
tags:
  - "express-js"
  - "route-handling"
  - "rest-api"
---

The basic building blocks of an API are routes. Routes define endpoints or urls to which an API can recieve HTTP requests.

Example of API routes:

{{<table "table table-striped table-bordered">}}

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Item 1   | Item 2   | Item 3   |
| Item 1a  | Item 2a  | Item 3a  |
{{</table>}}


**GET**  http://myapi.com/ - Homepage 

**GET**  http://myapi.com/users - list all users

**GET**  http://myapi.com/users/1 - show user whose ID is '1'

**POST** http://myapi.com/users - save a new user to the database

**PUT**  http://myapi.com/users/12 - update details of the user whose ID is '12'

The first part defines the HTTP method and the second part defines the API endpoint. Since all the endpoints have the same base URL we will be focusing on what comes after `.com`:

**GET**  /

**GET**  /users

**GET**  /users/1

**POST** /users

**PUT**  /users/12

In Express, we define our routes using the method `[http-method]()`on our API application (stored in the variable `app`) 

```js
// GET /users
app.get("/users",function(request,response){
   
})
// GET /users/1
app.get("/users/:id",function(request,response){

})

// POST /users
app.post("/users",function(request,response){

})

// POST /users/12
app.put("/users/12",function(request,response){

})
```