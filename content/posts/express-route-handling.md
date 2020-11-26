---
title: "Route Handling"
date: 2020-11-26T16:00:00+03:00
draft: false
toc: false
images:
tags:
  - "express-js"
  - "route-handling"
  - "rest-api"
---

The basic building blocks of an API are routes. Routes define endpoints or URLs to which an API can receive HTTP requests. 

Example of endpoints:

| HTTP method | Route                          | Description                                     |
| ----------- | ------------------------------ | ----------------------------------------------- |
| GET         | http://localhost:3000/users    | Return all users                                |
| GET         | http://localhost:3000/users/1  | Return user whose ID is 1                       |
| POST        | http://localhost:3000/users    | Save new user to the database                   |
| PUT         | http://localhost:3000/users/12 | Update information of the user with an ID of 12 |

### Resources

Before coming up with routes, we first need to identify resources within our API. Resources are data our API will be providing to its clients.

For instance, if we are to build an API responsible for providing information to a fast-food ordering mobile application, our API can have the following resources:

- Restaurants (restaurant name, location, contacts)

- Users (username, address, contact)

- Orders (restaurant, user, items)

By convention we will use nouns in their plural form to represent our resources.  The resources we come up with for our API can be directly mapped to the tables/collections our database will have.  

Using the resources we've defined above, we can start coming up with the routes for our API. A good rule of thumb is to create **CRUD** (Create,Read,Update,Delete) routes for each resource.

####   Restaurants' CRUD

| HTTP method | Route            | Description                                          |
| ----------- | ---------------- | ---------------------------------------------------- |
| POST        | /restaurants     | Return all users                                     |
| GET         | /restaurants     | Return user whose ID is 1                            |
| GET         | /restaurants/:id | Save new user to the database                        |
| PUT         | /restaurants/:id | Update information of the user with the ID specified |
| DEL         | /restaurants/:id | Delete restaurant with the ID specified              |
### Route Handling

To define a route using express we call the respective HTTP method on our `app` variable. Each method takes in 2 parameters, the route path, and a callback function which will be executed once a client makes the specified request to that route.

```app.[http-method]("route",callbackfunction)```

example:

```javascript
// HTTP method				callback function
//	 v								v
app.get("/restaurants",function(request,response){
//			   ^
//		 route(endpoint)   	
})

app.post("/restaurants",function(request,response){
	...
})
```

The callback function has two parameters:

- request - an object containing information about the request e.g data sent with the request 
- response - an object used to send a response to the client once they make the request

Here is an example of a route which sends back an array of restaurants when a **GET** request is made on the `/restaurants` endpoint:

```javascript
app.get("/restaurants",function(request,response){
	let restaurants = ["dominos","subway","kfc"]
    response.send({restaurants})
})
```

The `.send()` method is used to *send* back a response when a request is made to a particular route. When building our API  we will be sending back responses in the form of JSON (JavaScript Object Notation). To do so, we pass an object to the `.send()` method. 

#### Breakdown

`let restaurants = ["dominos","subway","kfc"]`

The assumption is that we have queried a database and got back an array of restaurants.

To send back a JSON response, we create an object which has a `restaurants` attribute whose value is an array of restaurants:

```javascript
{
	restaurants : ["dominos","subway","kfc"]
}

// the above can be shortened to
{restaurants}
```

The object is then passed as an argument to the `.send()` method.

``` javascript
response.send({restaurants})
```

### Route Parameters

Route parameters are used to define sections of a URL which will contain some data the API will need to process the request. For example, if we need our API to respond with a particular user depending on their user ID, we can define a route with the parameter `id`

```
GET /restaurants/:id
# 			 ^
#	 route parameter	
```

The above route will be matched to all the following requests:

``` 
GET http://localhost/restaurants/1
GET http://localhost/restaurants/2
GET http://localhost/restaurants/3
		  ...
```

Parameters in express are defined using the following syntax `:parameter-name` . A route can have multiple parameters:

```
GET /restaurants/:restid/employees/:empid
```

The above route can be used to retrieve a particular employee of a particular restaurant. The route below will return the information of the employee with an ID of `35` who works in a restaurant with an ID of `1` :

``` 
GET http://localhost/restaurants/4/employees/35
```

The request parameter values are stored in the `params ` object of the `request` object of route's callback function. 

```javascript
app.get("/restaurants/:id",function(request,response){
    let restaurantID = request.params.id 
    ...
})
app.get("/restaurants/:restid/employees/:empid",function(request,response){
    let restaurantID = request.params.restid 
    let employeeID = request.params.empid
    ...
})
```

### Query Strings

Almost similar to route parameters, however query strings are mostly used to "format" the response. For instance query strings can be used to filter,sort or limit the data sent back as a response. Query strings are optional and do not appear as part of the route definition. 

```
GET /restaurants
```

The above endpoint can have the following query parameters:

- limit - defines the maximum number of restaurants to send in the response
- sort - sort the results in ascending / descending order

Query parameters are defined at the end of the route by a question mark `?` then the query parameter name. They are specified by the client when making the request:

````
http://localhost:3000/restaurants?limit=10
http://localhost:3000/restaurants?sort=asc
````

Query parameters can be chained using the `&` symbol:

```
http://localhost:3000/restaurants?limit=10&sort=asc
```

To access the query parameters in express we use the `query` object of the `request` object of the route's callback function:

```javascript
app.get("/restaurants",function(request,response){
    let limit = req.query.limit
    let sort = req.query.sort
    ...
})
```

An important thing to note is that query parameters are optional, so you'll need to provide a default value in your code:

```javascript
app.get("/restaurants",function(request,response){
    let limit = 10 // default limit
    
    if(typeof(req.query.limit) != undefined){
        // if limit is specified
        limit = req.query.limit
    } 
    
    // short-form
    let limit = req.query.limit ? req.query.limit : 10
    //  			  ^		 			  ^			 ^
    //         is specified?         if true    if false
    
    let sort = req.query.sort ? req.query.sort : "asc"
    ...
})
```

### The API

```javascript
const express = require("express");
const app = express();

app.listen(3000,function(){
  console.log("Listening for requests on port 3000")
})

let DBrestaurants = ["subway","dominos","kfc"]

app.get("/restaurants",function(request,response){
    let limit = request.query.limit ? Number(request.query.limit) : 2
    let restaurants = DBrestaurants.slice(0,limit)
    response.send({restaurants})
})
app.get("/restaurants/:index",function(request,response){
	let restaurant = DBrestaurants[Number(request.params.index)]
    response.send({restaurant})
})
```

Now we can create a simple API capable of responding to GET requests using query strings and route parameters.

Try the following routes on the browser. JSON viewer extension for [Chrome](https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en) and  [Mozilla](https://addons.mozilla.org/en-US/firefox/addon/jsonview/).

```
http://localhost:3000/restaurants
http://localhost:3000/restaurants?limit=2
http://localhost:3000/restaurants/2
```

### Wrap Up

An important thing to note is that all data sent via HTTP (including query strings and parameters) are in text form (string data type). To user the limit query and index parameter we need to cast them to the Number datatype. This is achieved using the function `Number()`

```javascript
Number(request.params.index)

Number(request.query.limit)
```

Next up will be handling POST and PUT request using express. 

> Imperviable growth now, brings exponential growth later.

Cheers.

