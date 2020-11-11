---
title: "Callback Functions"
date: 2020-11-01T12:00:00+03:00
draft: false
toc: false
images:
tags:
  - "callback-functions"
  - "javascript"
---

Callback functions are quite common when programming with Javascript. As the name suggests, these are functions which are called after a certain task is completed. Callbacks are passed to other functions as arguments and are executed once a certain task has finished execution.

An example of a scenario where callback functions can be used is when retrieving records from a database.


Let's first define our callback function.

```javascript
function printName(name){
  console.log(name);
}
```

`printName` should be called once we retrieve a record from the database. The function takes in a `name` parameter and logs it onto the console.


Our second function, `findUser` is responsible for querying the database and finding a `user` based on the `userId` field. This function takes in two parameters, the `userID` and `printName` (a callback function). 

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


We want to print the user's name once we find the record. So after getting a result from the database, we call the function `printName` and pass the name property of the user object as an argument.

### Arguments vs Parameters

An argument is data we pass to function when calling it while a parameter is a local variable defined inside a function (can only be accessed inside the function)

```js
//              parameter     
//                  v
function printName(name){
  console.log(name)
}

console.log(name) // Uncaught ReferenceError: name is not defined

// Calling the function
printName("edwin") // output: "edwin"
//           ^
//        Argument 

```

### Calling the function

There are two ways in which we can call the function `findUser`. Either by passing our predefined function `printName` as an argument:

```javascript
findUser(1,printName)
//       ^     ^
//   userID  callback
```

or by defining the function on the argument list.

```javascript
findUser(1,function(username){
  console.log(username)
});

// Using arrow functions
findUser(1,(username)=>{ 
  console.log(username)
})
```

Both of these are valid methods of using callback functions. However, you'll find that I'll be opting for defining the function on the argument (just preference).

### Array.ForEach

Another scenario where callback functions are used is in Array's `forEach` method.

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

As the method's name suggests, *for each* item in the array, call this function. In our case, we have defined the function on the argument list which takes each item in the array and prints it on the console.

### Wrap up

Callbacks are functions which are passed as arguments to other functions. They are then exected inside the function in which it was passed to. Most of the time we will be interacting with built-in functions which have callbacks as arguments (`Array.ForEach`), instead of defining our own functions (`findUser`) which take in callbacks as arguments.

Callback functions are heavily used in Javascript so an understanding of what they are and when to use them goes a long way.

Next up, we finally get to build a REST API. Hold on tight.

Cheers. 
