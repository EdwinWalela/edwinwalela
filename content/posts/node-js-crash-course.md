---
title: "Node JS crash course"
date: 2020-11-06T13:00:00+03:00
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
There are numerous code editors available but I prefer [Visual Studio Code](https://code.visualstudio.com/) due to the extensions it has to offer which makes coding a breeze.

We shall first create a directory for our project

```bash 
mkdir node-crashcourse

cd node-crashcourse
```

Once inside our folder we need to initialize our Node JS project.

```bash
npm init
```

 This will take us through the process of setting up our project. 
 
 First we define a project name. The project already has a default name so we can proceed by pressing `enter`.

 There is also no need of specifying the version, so proceed by pressing `enter`. The description field will help others who might interact with this project to know what it's about.

 The entry point we shall leave it as `index.js`. Skip the test command, git repository and keywords using `enter`. Once done, you'll be prompted to confirm, hit the `enter` key to accept the changes. 
 
 Later on, we will be using the command `npm install` to install 3rd-Party libraries and frameworks.


### Hello world

It's time to write our first line of code in Javascript.

Create a new file `index.js`

To print `hello world` on the console we shall type this line of code.

```Javascript
console.log("hello world")
```

Save the file and run the command `node [file-name].js`. So for this case the command will be :

```bash
node index.js
```

### Javascript Cheat Sheet

We will now go through the basics of the Javascript language. As I mentioned earlier, Node JS is just an *environment* of executing Javascript Code.

This cheat sheet only covers the basics and its purpose is to act as reference material. Prior programming experience in whichever language is essential.


#### Variables 

```js
let age = 10
let weight = 27.439 
let name = "edwin"
let isExpired = false
const password = "@(*jaKA.?!"

age = 11 // Changing the value of a predefined variable

password = "!23.3@=PO&" // This will throw an error (constant variables can not be changed)
```

#### Objects

```js
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
console.log(carsArr[0].model) // bmw
```

#### Loops
```js
for(let x = 0; x < 10;x++){
  console.log(x)
}

let arr2 = [1,2,3,4,5]
let length = arr2.length; // Get array length
let i = 0;

while(i < length){
  console.log(numbers[i])
  i++; // Increment i by 1
}
```

#### IF statements

```js
let userAge = 11
let skill = "html"

if(userAge < 18){
  console.log("Minimum age requirement not reached")
}else{
  console.log("Minimum age requirement reached")
}

// AND operator (&&)

if(userAge > 18 && skill == "html"){
  console.log("Both requirements met")
}

// OR operator (||)
if(userAge > 18 || skill == "html"){
  console.log("One requirement met")
}
```

#### Functions

```js
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
```

#### Arrays

```js
let numbers = [1,2,3,4,5,6];

let arrLength = numbers.length // Get array length = 6

// Add item to array
numbers.push(7) // [1,2,3,4,5,6,7]

// Remove last item from array
numbers.pop() // [1,2,3,4,5,6]

// Loop through array 
person.skills.forEach(function(skill){
  console.log(skill)
})
// or (using an arrow function)
person.skills.forEach((skill)=>{
  console.log(skill)
})
```

#### String concatenation
```js
let experience = 5;

console.log("You need to have minimum "+experience+" years to qualify")
console.log(`You need to have minimum ${experience} years to qualify`)
```

#### Classes

```js
class Person{
  // Method called when we instantiate the class (create an object)
  constructor(name,skills){
    // properties
    this.name = name;
    this.skills = skills
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
let isVerified = person1.verified; // false

if(isVerified == true){
  console.log("user is verified")
}else{
  console.log("User is not verified")
}
// The above code can be shortened to
if(isVerified){
  console.log("user is verified")
}else{
  console.log("User is not verified")
}

// Calling a method of the object
person1.verify();

isVerified = person1.verified; // true

if(isVerified){
  console.log("user is verified")
}else{
  console.log("User is not verified")
}
```

This isn't a complete tutorial on the Javascript Language, but it should smoothen the path ahead. Next up will be Javascript callback functions before we start building an API.

Cheers.