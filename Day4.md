# Day 4: 

This README file summarizes all of functions, Events & Handler 

## Lesson Summary

### Function 
#### What is Function? 
A JavaScript function is a block of code designed to perform a particular task. And executed when invokes it (calls it).

#### NOTES:💡
1. values are things
2. variables point to things
3. functions do things

#### What is difference between parameters and arguments? 
parameters are the inputs a function expects
arguments are the actual values the function is called with

#### What is retunr value? 
Return values-> A return statement specifies the function's output value
> The default return value of JS functions is `undefined`, so if a function doesn't have a `return` the return value of it will be `undefined`.


```javaScript
function add(x, y) { // x,y are parameters 
  return x + y
}
add(2,3) // 2,3 are arguments 
```
```javaScript
function add(x,y,z){
    return x+y+z;
}
add(1,2); //NaN
/*
cuz we didn't pass the 3rd argument >>> JS will take it as undefined value 
1+2+undefined= NaN >>> NaN is (not a number)
typeof NaN = "number" 
ex: 0/ 0 = NaN
*/
```
```javaScript
function getRandomNumber(){
    return Math.random();
}
getRandomNumber("sth"); //0.56259486521546513
/*
JS will ignore that we passed an argument even when it doesn't have parameters
*/
```

#### How u can define function in JS? 
1. function() keyword
2. Arrow function =>


#### What is arrow function? 
It help create an unnamed function without much code when we just want to return a value. 
* For one-parameter functions, parentheses are optional
* For multiple parameters, parentheses are required

> If we need to do more than just return a value, we can use curly braces for a "normal" function body
> this keyword will have differents behavior when using it with noraml function than use it with arrow function (use MDN for that)

Since arrow functions are expressions, we can assign them to a variable:
```javascript
const add = (x,y) => x + y;
is equivelant to

function add (x,y){
  return  x + y; //RETURN
}
```

### Scope
#### What is Scope? 
The scope is the current context of execution in which values and expressions are "visible" or can be referenced. If a variable or expression is not in the current scope, it will not be available for use. 

> Note: Scopes can also be layered in a hierarchy, so that child scopes have access to parent scopes, but not vice versa.

Variables declared with let can be modified from within a narrower scope (nested) not wider 

- var: Variables declared with var are in the function scope 
- let: Variables declared as let are in the block scope
- const: Variables declared as const are in the block scope


### Events & Handler 
#### What is Events? 
Events are the way to make our web page interactive!

#### NOTES:💡
1. The web browser fires events when certain things happen on the page
2. For example, when the user clicks somewhere on the page, a click event is fired
3. We can detect events with JS using an event listener, The .addEventListener() method lets us listen for events on a DOM element
```javascript 
document.addEventListener("click", () => {
    console.log("clicked")
});
```

#### How we can handel Events? 
.addEventListener() takes 2 parameters:
1. The name of the event to listen to (e.g. "click")
2. A handler function that JS calls when that event is fired on this element

JS passes an event object to the handler function with information about the eventv (this is optional)
> WE accept this as a parameter, we can use it to get details 
```javascript 
document.addEventListener("click", (event) => {
    console.log(event)
});
```
"click", "dblclick","mouseover,"mouseout", ...-> type of event we can handle


## Coding Exercises and my Solution:

1. [Global Scope and Functionsr](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)
```javascript
let myGlobal=10;
function fun1() {
  oopsGlobal=5 // Variables defined without let or var keyword become global variables. And 
}
```


2. [Local Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)
```javascript
function myLocalScope() {
  let myVar;
  console.log('inside myLocalScope', myVar);
}
myLocalScope();

console.log('outside myLocalScope', myVar);
```


3. [Global vs. Local Scope in Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions)
```javascript
const outerWear = "T-Shirt";

function myOutfit() {
  const outerWear = "sweater";
  return outerWear;
}

myOutfit();
```


4. [Stand in Line](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/stand-in-line)
#### My Solution
```javascript
function nextInLine(arr, item) {
  arr.push(item);
  item=arr.shift()
  
  return item;
}
```
