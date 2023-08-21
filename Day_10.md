# Day 10:

This README file summarizes the Classes & Prototypes

## Lesson Summary

### Classes & Prototypes

#### Objects
JavaScript objects are complex data structures that allow developers to store and access data in a key-value format. An object is an unordered collection of properties, where each property has a name (or key) and a value. The keys are usually strings, but they can also be symbols, and the values can be any data type, including other objects.

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

#### In JavaScript we can create an object in one of four ways: 
1- Object literal notation
2- Using the new Object() constructor
3- Using a constructor function
4- Using class

## JavaScript Classes
Classes are one of the features introduced in the **ES6** version of JavaScript. You can think of the class as a sketch (prototype) of an object. And then we can create many objects of that (prototype).

## Prototype
In JavaScript, a **prototype** is a mechanism that allows objects to inherit properties and methods from other objects. Every object in JavaScript has a prototype, which can be either another object or `null`. When a property or method of an object is accessed, JavaScript first looks for that property or method in the object itself. If it is not found, it looks for it in the object's prototype, and keeps looking

Every Object in JavaScript has a prototype, we need that prototype to keep track of the attributes in that object/function and to inherit those attributes to child objects.

### Prototype Chain
When a property or method of an object is accessed in JavaScript, the language first looks for that property or method in the object itself. If it is not found, it looks for it in the object's prototype, and keeps looking up the prototype chain until the property or method is found or the end of the chain is reached. 

Prototype chaining allows objects to inherit properties and methods from other objects.
![image](https://github.com/AnwarMelhem/Mastering_JavaScript_in_20_Days/assets/97465642/d3e08c6a-1ab7-456d-8c80-8b2f366d99ed)


## Object.prototype.hasOwnProperty()
The hasOwnProperty() method of Object instances returns a boolean indicating whether this object has the specified property as its own property (as opposed to inheriting it).


### [Coding Exercises](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%204/task.md)

26 exercises of the Object Oriented Programming section soluation in this link ->[Soluations](https://www.freecodecamp.org/WaleedZriqui)
