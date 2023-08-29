# Day 7:

This README file summarizes JavaScript principles, Callbacks & Higher Order functions 

## Lesson Summary

### JavaScript principles (How will code run in JS):
When JavaScript code runs, it:
- Goes through the code line-by-line and runs/ ’executes’ each line - known as the thread of execution
- Saves ‘data’ like strings and arrays so we can use that data later - in its memory. We can even save code (‘functions’)

### Execution context
Code we save (‘define’) functions & can use (call/invoke/execute/run) later with the function’s name & ( )

Functions Created to run the code of a function - has 2 parts
- Thread of execution
- Memory

###  Call Stack (LIFO)
call stack-> JavaScript keeps track of what function is currently running (where’s the thread of execution)
- Run a function, add to call stack
- Finish running the function, JS removes it from call stack
- Whatever is top of the call stack that’s the function we’re currently running

> Note: when the slack is empty then we are running code in global() which is under stack

### DRY Princeple -> Don't Repeat your self "One of Fundamental principle programming"

### Generalizing functions
- We can generalize the function to make it reusable
- ‘Parameters’ (placeholders) mean we don’t need to decide what data to run our functionality on until we run the function-> Then provide an actual value (‘argument’) when we run the function

### Callback function
A callback function is a function passed into another function as an argument, which is then invoked inside the outer function to complete some kind of routine or action.

```javascript 
function copyArrayAndManipulate(array, instructions) {
  const output = [];
  for (let i = 0; i < array.length; i++) {
    output.push(instructions(array[i]));
  }
  return output;
}
function multiplyBy2(input) { return input * 2; }
function divideBy2(input) { return input / 2; }
const result = copyArrayAndManipulate([1, 2, 3], multiplyBy2);
const result = copyArrayAndManipulate([1, 2, 3], divideBy2);
```

From code above which is our Higher Order Function?
- The outer function that takes in a function is our higher-order function (copyArrayAndManipulate)

From code above which is our Callback Function
- The function we insert is our callback function (multiplyBy2, divideBy2)

### Functions in javascript = first class objects (Explian is 1-3 below 👇)
They can co-exist with and can be treated like any other javascript object
1. Assigned to variables and properties of other objects
2. Passed as arguments into functions
3. Returned as values from functions

> Note: Callbacks and Higher Order Functions simplify our code and keep it DRY

### Arrow function expressions
An arrow function expression is a compact alternative to a traditional function expression, with some semantic differences and deliberate limitations in usage (It's also a shorthand way to save our code by ES6)
```javascript 
const multiplyBy2 = input => input*2 // because it's one attribure here and one row for the code
```


## Coding Exercise and my Solution:

### [Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-higher-order-functions-map-filter-or-reduce-to-solve-a-complex-problem)
```javascript
const squareList = arr => {
  return arr.filter(num => (num > 0 && num % parseInt(num) == 0))
            .map(num => Math.pow(num, 2));
};
```

### [Apply Functional Programming to Convert Strings to URL Slugs](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/apply-functional-programming-to-convert-strings-to-url-slugs)
```javascript
function urlSlug(title) {
return title.toLowerCase()
            .trim()
            .split(' ')
            .filter(s=>s!= "")
            .join('-')
}
```

### [Question 1: Functions and Callbacks](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%201/tasks.md)
``` javascript
async function mapAsync(array, callback) {
  const results = [];
  
  for (let i = 0; i < array.length; i++) {
    const result = await callback(array[i]);
    results.push(result);
  }

  return results;
}
```

### [Question 2: Call Stack and Recursion](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%201/tasks.md)
``` javascript
function sumRange(num1, num2) {
    if (num1>num2){
        return 0
    }else{
        return num1 + sumRange(num1+1, num2)
    }
}
```
