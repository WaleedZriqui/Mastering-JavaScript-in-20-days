# Day 7:

## Lesson Summary

### JavaScript principles:
When JavaScript code runs, it:
Goes through the code line-by-line and runs/ ’executes’ each line - known as the thread of execution
Saves ‘data’ like strings and arrays so we can use that data later - in its memory
We can even save code (‘functions’)

Functions Created to run the code of a function - has 2 parts
- Thread of execution
- Memory
  
Execution context
Code we save (‘define’) functions &
can use (call/invoke/execute/run)
later with the function’s name & ( )

###  Call Stack
call stack-> JavaScript keeps track of what function is currently running (where’s the thread of execution)
- Run a function - add to call stack
- Finish running the function - JS removes it from call stack
- Whatever is top of the call stack that’s the function we’re currently running

### DRY-> Don't Repeat your self ->fundamental principle programming

### We can generalize the function to make it reusable

### Generalizing functions
‘Parameters’ (placeholders) mean we don’t need to decide what data to run our
functionality on until we run the function->Then provide an actual value (‘argument’) when we run the function

### Callback function
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

There are two ways in which the callback may be called: synchronous and asynchronous. Synchronous callbacks are called immediately after the invocation of the outer function, with no intervening asynchronous tasks, while asynchronous callbacks are called at some point later, after an asynchronous operation has completed.

# Which is our Higher Order Function?
The outer function that takes in a function is our higher-order function

# Which is our Callback Function
The function we insert is our callback function


## Functions in javascript = first class objects
They can co-exist with and can be treated like any other javascript object
1. Assigned to variables and properties of other objects
2. Passed as arguments into functions
3. Returned as values from functions

## Arrow function expressions
An arrow function expression is a compact alternative to a traditional function expression, with some semantic differences and deliberate limitations in usage

*********************************************************************************************************************
## Coding Exercises

### [Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-higher-order-functions-map-filter-or-reduce-to-solve-a-complex-problem)
```javascript
const squareList = arr => {
  const arr1= arr.filter(num => num > 0 && num % parseInt(num) === 0)
          .map(num => Math.pow(num, 2));
  return arr1

};

const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
console.log(squaredIntegers);
```

### [Apply Functional Programming to Convert Strings to URL Slugs](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/apply-functional-programming-to-convert-strings-to-url-slugs)
```javascript
function urlSlug(title) {
return title
    .split(" ")
    .filter(substr => substr !== "")
    .join("-")
    .toLowerCase();
}
urlSlug("A Mind Needs Books Like A Sword Needs A Whetstone");
```
### [Question 1: Functions and Callbacks](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%201/tasks.md)
``` javascript
async function mapAsync(array, instructions) {
    const output = [];
    for (let i = 0; i < array.length; i++) {
    output.push(await instructions(array[i]));
    }
    return output;
   }
   async function multiplyBy2(input) { return input * 2; }
   const result = mapAsync([1, 2, 3, 4, 5],  multiplyBy2)
   .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```