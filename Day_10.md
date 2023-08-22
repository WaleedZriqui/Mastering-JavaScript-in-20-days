# Day 10:

This README file summarizes the Classes & Prototypes

## Lesson Summary

### Classes & Prototypes

#### JavaScript Classes
Classes are one of the features introduced in the **ES6** version of JavaScript. You can think of the class as a sketch (prototype) of an object. And then we can create many objects of that (prototype).

#### Objects
JavaScript objects are complex data structures that allow developers to store and access data in a key-value format. An object is an unordered collection of properties, where each property has a name (or key) and a value. The keys are usually strings, but they can also be symbols, and the values can be any data type, including other objects.

#### In JavaScript we can create an object in one of four ways: 
1- Object literal notation
2- Using the new Object() constructor
3- Using a constructor function
4- Using class

```javascript
const user1 = {
 name: "Will",
 score: 3,
 increment: function() { user1.score++; }
};
user1.increment(); //user1.score -> 4
```
```javascript
const user2 = {}; //create an empty object
//assign properties to that object
user2.name = "Tim";
user2.score = 6;
user2.increment = function() {
 user2.score++;
};
```
```javascript
const user3 = Object.create(null);
user3.name = "Eva";
user3.score = 9;
user3.increment = function() {
 user3.score++;
};
```
> Our code is getting repetitive, we're breaking our DRY principle

#### Solution 1. Generate objects using a function
```javascript
function userCreator(name, score) {
    const newUser = {};
    newUser.name = name;
    newUser.score = score;
    newUser.increment = function() {
    newUser.score++;
    };
    return newUser;
};
const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment()
```
* **Problems**: Each time we create a new user we make space in our computer's memory for all our data and functions. But our functions are just copies (i.e. lets consider that the above function is 100 rows of code, then i will waste memory and space)

#### Solution 2: Using the prototype chain
```javascript
function userCreator (name, score) {
    const newUser = Object.create(userFunctionStore);
    newUser.name = name;
    newUser.score = score;
    return newUser;
};
const userFunctionStore = {
    increment: function(){this.score++;},
    login: function(){console.log("Logged in");}
};
const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();
```
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/d6ed45af-6037-4f71-9c85-7b353b1f6795)
* Here const objectA = Object.create(otherObject), objectA will get a link to the otherObject. So if we don't find a property in objectA then it will also go to other function. And that happening by define a '__proto__' inside the object objectA will link to the other object  
* The main point here is using the `this` keyword to be accessed by other objects 
> Note: Don't forget a backpack in the above example 

#### Prototype
In JavaScript, a **prototype** is a mechanism that allows objects to inherit properties and methods from other objects. Every object in JavaScript has a prototype, which can be either another object or `null`. When a property or method of an object is accessed, JavaScript first looks for that property or method in the object itself. If it is not found, it looks for it in the object's prototype, and keeps looking

- Every Object in JavaScript has a prototype, we need that prototype to keep track of the attributes in that object/function and to inherit those attributes to child objects.
- All objects have a __proto__ property by default which defaults to linking to a big object - `Object.prototype` full of (somewhat) useful functions. And even if it will link to other object it will still link to the big object 

### Prototype Chain
When a property or method of an object is accessed in JavaScript, the language first looks for that property or method in the object itself. If it is not found, it looks for it in the object's prototype, and keeps looking up the prototype chain until the property or method is found or the end of the chain is reached. 

Prototype chaining allows objects to inherit properties and methods from other objects.

#### Object.prototype.hasOwnProperty()
The hasOwnProperty() method of Object instances returns a boolean indicating whether this object has the specified property as its own property (as opposed to inheriting it).

### This keyword 

When we call user1.increment(). In local meomory this atriburte is saved with value 'user1' 

```javascript
function userCreator (name, score) {
    const newUser = Object.create(userFunctionStore);
    newUser.name = name;
    newUser.score = score;
    return newUser;
};
const userFunctionStore = {
    increment: function() {
        function add1(){ this.score++; }
        add1()
    }
};
const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();
```
What does `this` auto-assigned to?
Here this will not get the value of user1 
* The soultion can be done by using the add1.call(this), .call() can be used to invoke (call) a method with an owner object as an argument (parameter). 

Unlike regular functions, arrow functions do not have their own this . The value of this inside an arrow function remains the same throughout the lifecycle of the function and is always bound to the value of this in the closest non-arrow parent function.
```javascript
const userFunctionStore = {
    increment: function() {
        const add1 = () => { this.score++; }
        add1()
    }
};
user1.increment();
```
So here unlike the regular function, the arrow function will go to the parent and used value for 'this' and in this case it's "user1"

#### Solution 3 - Introducing the keyword that automates the hard work: new
All the hard work doing above can be replaced by 'new' keyword  
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/afc45ffb-4080-44c5-837e-e6ff4e1fa8d7)

When we call the function that returns an object with new in front we automate 2
things
1. Create a new user object
2. Return the new user object

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/fda6cfcb-3434-45f3-b626-44194a44467d)

```javascript
function userCreator (name, score) {
    this.name = name;
    this.score = score;
};
userCreator.protoype.increment: function(){this.score++;},
userCreator.protoype.login: function(){console.log("Logged in");}

const user1 = userCreator("Eva", 9);
user1.increment();
```
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/d6c2a76d-7265-48ce-a24c-27b9b6eb3dd1)


#### Solution 4: The class ‘syntactic sugar’
In the solituon 3 we are writing our shared methods separately from our object ‘constructor’ itself (off in the userCreator.prototype object)
Other languages let us do this all in one place. ES2015 lets us do so too by using class keyword and constructor 

```javascript
class UserCreator {
    constructor (name, score){ 
        this.name = name;
        this.score = score;
    }
    increment: function(){this.score++;},
    login: function(){console.log("Logged in");}
}
const user1 = userCreator("Eva", 9);
user1.increment();
```
Nothing in excution will change ^-^. Class is a function object, function -> constroctor, protoztypes will stay as them 


## Coding Exercise and my Solution:

### [Coding Exercises](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%204/task.md)

26 exercises of the Object Oriented Programming section soluation in this link ->[Soluations](https://www.freecodecamp.org/WaleedZriqui)
