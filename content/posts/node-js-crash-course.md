---
title: "Node JS crash course"
date: 2020-09-02T12:36:39+03:00
draft: false
toc: false
images:
tags:
  - "cheat-sheet"
  - "tutorial"
  - "javascript-tutorial"
  - "node-js-tutorial"
---

Node JS is a Javascript runtime environment which executes Javascript code outside a web browser. With Node, we are able to write and run Javascript on the console on any operating system. This is what enables Node JS to be used in writing server-side applications.

Node JS isn't a programming language but an environment where Javascript code is executed. In this case, the environment of execution is the terminal. Javascript can also be executed on the browser (another environment of execution).


### Installing Node JS

To install Node JS, head over to their [homepage](https://nodejs.org/en/download/). For Windows and macOS users, download the respective Installer and follow the prompts.

For Linux users, you can either download the binary files from the homepage or use the following commands

```bash
sudo apt install nodejs

sudo apt install npm
```

To verify if the installation was a success run this command. The output should be the version of Node and NPM installed.

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

 This will take through the process of seting up our project. First we define a name for our project. The name already has a default name so we can procceed by pressing `enter`.

 There is also no need of specifying the version, so procceed by pressing `enter`. The description field will help others who might interact with this project to know what it's about.

 The entry point we shall leave it as `index.js`. Skip the test command, git repository and keywords using `enter`.

 Once we are done, we will be prompted to confirm our input, so hit the `enter` key.


### Hello world

It's time to write our first line of code in Javascript.

Create a new file `index.js`

To print `hello world` onto the console we shall type this line of code.

```Javascript
console.log("hello world")
```

Save the file and run the following command

```bash
node index.js
```

### Javascript Cheat Sheet

We will now go through the basics of the Javascript language. As I mentioned earlier, Node JS is just an *environment* of executing Javascript Code.

This cheat sheet only covers the basics and it's purpose is to act as refference material. Prior programming experience in whichever language is essential.

```javascript
// Variables
let age = 10
let name = "edwin"
let isExpired = false

// Arrays
let arr = [1,2,3,0.6,9,11.830]
let cars = ["toyota","bmw", "honda"]

// Objects
let person = {
  age:15,
  nationality:"Kenyan",
  skills:["javascript","php","java"],
  isRegistered:false
}

console.log(person.age) // 15
console.log(person.skills[2]) // java
console.log(person.isRegistered) // false

person.skills.push("c++") // Insert item to an array

console.log(person.skills) // [ 'javascript', 'php', 'java', 'c++' ]

// Loops
for(let i = 0; i < person.skills.length; i++){
  console.log(person.skills[i])
}

person.skills.forEach(skill=>{
  console.log(skill)
})

// If statements
if(person.age < 18){
  console.log("Minimum age requirement not reached")
}else{
  console.log("Minimum age requirement reached")
}

// Functions
function sum(x,y){
  return x + y
}

let result = sum(3,4)

console.log("3 + 4 = "+result)   // 3 + 4 = 7
console.log(`3 + 4 = ${result}`) // 3 + 4 = 7

// String concatenation
let experience = 5;

console.log("You need to have minimum "+experience+" years to qualify")
console.log(`You need to have minimum ${experience} years to qualify`)
```

This isn't a complete tutorial on the Javascript Language, but it should smoothen the path ahead. 