---
title: "Callback Functions"
date: 2020-11-01T12:00:00+03:00
draft: false
toc: false
images:
tags:
  - "Callbacks"
  - "Node JS"
  - "Javascript"
---

Callback functions are quite common when programming with Javascript. As the name suggests, these are functions which are called after a certain task is completed. Callbacks are passed to other functions as parameters and are executed once the function it was passed into has finished execution.

An example of a scenario where callback functions can be used is when retrieving records from a database.


Let's first define our callback function.

```javascript
function printName(name){
  console.log(name);
}
```

`printName` will be called once we retrieve a record from the database. The function takes in a parameter `name` and logs it onto the console.


Our second function, `findUser` is responsible for querying the database and finding a `user` based on the `userId` field. 

`findUser` takes in two parameters, the `userID` and `printName` (a callback function). 

```javascript
function findUser(userId,printName){ 
  // Query database and retrieve user
  // let user = DB.findByID(userId)

  // Result from querying the database
  let user = {
    name:"edwin",
    email:"edwin@mail.com"
  }
  // Now print the name of the user
  printName(user.name);
}
```


We want to print the user's name once we find the record. So after getting a result from the database, we call the function `printName`

There are two ways in which we can call the function `findUser`. Either by passing our predefined function `printName` as a parameter

```javascript
findUser(1,printName)
```

or by defining the function on the parameter list.

```javascript
findUser(1,function(username){
  console.log(username)
});

// Using arrow functions
findUser(1,(username)=>{ 
  console.log(username)
})
```

Both of these are valid methods of using callback functions. However, you'll find that I'll be opting for the second method (just prefference).

Another scenario where callback functions are used is in Arrays `forEach` method.

```javascript
let arr = ["🍊","🍍","🍏"]

arr.forEach(function(fruit){
  console.log(fruit)
})
// or
arr.forEach((fruit)=>{
  console.log(fruit)
})

// Output : 🍊 🍍 🍏
```

As the method's name suggests, *for each* item in the array, call this function. In our case, we have defined the function on the parameter list which takes in an single item in the array and prints it to the console.

Callback functions are heavily used in Javascript so an understanding of what they are and when to use them goes a long way.

Next we will look at Promises before starting on building a REST API.

Cheers.
