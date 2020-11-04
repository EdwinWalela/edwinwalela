---
title: "Node JS crash course"
date: 2020-11-03T09:00:00+03:00
draft: false
toc: false
images:
tags:
  - "cheat-sheet"
  - "tutorial"
  - "javascript"
  - "node-js"
---

Node JS is a Javascript runtime environment which executes Javascript code outside a web browser. With Node, we are able to write and run Javascript on the console on any operating system. This is what enables Node JS to be used in writing server-side applications.

Node JS isn't a programming language but an environment where Javascript code is executed. In this case, the environment of execution is the terminal. Javascript can also be executed on the browser (another environment of execution).


### Installing Node JS

To install Node JS, head over to their [homepage](https://nodejs.org/en/download/). For Windows and macOS users, download the respective Installer and follow the prompts.

For Linux users, you can either download the binary files from the homepage or use the following commands

```bash
sudo apt install nodejs
```
```bash
sudo apt install npm
```

To verify if the installation was a success run these commands. The output should be the version of Node and NPM installed.

```
node -v 
```

```
npm -v
```

### Project Setup
We shall first create a directory for our project

```bash 
mkdir node-crashcourse

cd node-crashcourse
```

Once inside our folder we need to initialze our Node JS project.

```bash
npm init
```

 This will take through the process of seting up our project. First we define a name for our project. The project already has a default name so we can procceed by pressing `enter`.

 There is also no need of specifying the version, so procceed by pressing `enter`. The description field will help others who might interact with this project to know what it's about.

 The entry point we shall leave it as `index.js`. Skip the test command, git repository and keywords using `enter`. Once done, you'll be prompted to confirm, hit the `enter` key to accept the changes. 
 
 Later on, we will be using the command `npm install` to install 3rd-Party libraries.


### Hello world

It's time to write our first line of code in Javascript.

Create a new file `index.js`

To print `hello world` onto the console we shall type this line of code.

```Javascript
console.log("hello world")
```

Save the file and run the command `node [file-name].js`. So for this case the command will be :

```bash
node index.js
```

### Javascript Cheat Sheet

We will now go through the basics of the Javascript language. As I mentioned earlier, Node JS is just an *environment* of executing Javascript Code.

There are numerous code editors available but I prefer [Visual Studio Code](https://code.visualstudio.com/) due to the extensions it has to offer which makes coding a breeze.

This cheat sheet only covers the basics and it's purpose is to act as refference material. Prior programming experience in whichever language is essential.

```javascript
// Declaring variables
let age = 10
let name = "edwin"
let isExpired = false
const password = "@(*jaKA.?!"

age = 11 // Changing the value of a predefined variable

password = "!23.3@=PO&" // This will throw an error (constant variables can not be changed)

//--  Arrays --//

let arr = [1,2,3,0.6,9,11.830]
let cars = ["toyota","bmw", "honda"]

// Objects
let person = {
  age:15,
  nationality:"Kenyan",
  skills:["javascript","php","java"],
  isRegistered:false
}

// Array of objects
let carsArr = [
  {
    year:2003,
    model:"bmw"
  },
  {
    year:2001,
    model:"honda"
  }
]

console.log(person.age) // 15
console.log(person.skills[2]) // java
console.log(person.isRegistered) // false
console.log(person.skills) // [ 'javascript', 'php', 'java', 'c++' ]

//-- Loops --//

for(let x = 0; x < 10;x++){
  console.log(x)
}

let arr2 = [1,2,3,4,5]
let length = arr2.length; // Get array length
let i = 0;

while(i > length){
  console.log(numbers[i])
  i++; // Increment i by 1
}

//-- If statements --//

let userAge = 11

if(userAge < 18){
  console.log("Minimum age requirement not reached")
}else{
  console.log("Minimum age requirement reached")
}

//-- Functions --//

function sum(x,y){
  return x + y
}
// or (using an arrow function)
sum = (x,y) =>{
  return x + y
}

// Calling a function and storing the return value in a variable
let result = sum(3,4)

console.log("3 + 4 = "+result)

//-- Array methods --//

let numbers = [1,2,3,4,5,6];

let arrLength = numbers.length // Get array length = 6

numbers.push(7) // [1,2,3,4,5,6,7]

numbers.pop() // [1,2,3,4,5,6]

// Loop through array 
person.skills.forEach(function(skill){
  console.log(skill)
})
// or (using an arrow function)
person.skills.forEach((skill)=>{
  console.log(skill)
})

// String concatenation
let experience = 5;

console.log("You need to have minimum "+experience+" years to qualify")
console.log(`You need to have minimum ${experience} years to qualify`)

//-- Classes --//

class Person{
  // Method called when we instantiate the class (create an object)
  constructor(name,skills){
    // properties
    this.name = "";
    this.skills = []
    this.verified = false;
  }
  // methods (functions)
  verify(){
    this.verified = true;
  }
}
// Creating an object (an instance of a class)
let person1 = new Person("edwin",["html","css"])
let person2 = new Person("walela",["php","python"])

//Accessing a property of the object
let isVerified = person1.verified;

if(isVerified){
  console.log("user is verified")
}else{
  console.log("User is not verified")
}

// Calling a method of the object
person1.verify();

if(isVerified){
  console.log("user is verified")
}else{
  console.log("User is not verified")
}
```

This isn't a complete tutorial on the Javascript Language, but it should smoothen the path ahead. 

Cheers.