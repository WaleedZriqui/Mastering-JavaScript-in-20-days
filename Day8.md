# Day 8: 

This README file summarizes Clousers 

## Lesson Summary

### Clousers 
In JavaScript, closures are an important concept that allows functions to access variables from their outer lexical environment even after the outer function has finished executing. It all starts with us returning a function from another function

```javascript
function createFunction() {
  function multiplyBy2 (num){
    return num*2;
  }
  return multiplyBy2;
}
const generatedFunc = createFunction();
const result = generatedFunc(3);
//here generatedFunc() has a definition of function multiplyBy2() as a result of excution one time for createFunction()
```

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/8f7ccb83-e4a2-490f-9674-cf448e75ba89)

#### Notes: 💡
- We can declear variables and saved then inside running of another function. Not used there but instead returned them out 
- A closure is created when an inner function is returned from an outer function and still has access to its lexical scope, including the variables and parameters of the outer function.
- A closure is a function that preserves the outer scope in its inner scope.

Closures are powerful because they allow functions to retain access to the variables they need, even when they are invoked outside their original lexical scope. This behavior enables advanced patterns and techniques in JavaScript programming.

- Lexical scoping describes how the JavaScript engine uses the location of the variable in the code to determine where that variable is available.
- A closure is a combination of a function and its ability to remember variables in the outer scope.

### Functions with memories
-the Functions get a new memory every run/invocation
- When our functions get called, we create a live store of data (local
memory/variable environment/state) for that function’s execution context.
- When the function finishes executing, its local memory is deleted (except the
returned value)

### Calling a function in the same function call as it was defined
```javascript
function outer (){
 let counter = 0;
 function incrementCounter (){
 counter ++;
 }
 incrementCounter();
}
outer();
```
### Calling a function outside of the function call in which it was defined
```javascript
function outer (){
 let counter = 0;
 function incrementCounter (){ counter ++; }
 return incrementCounter;
}
const myNewFunction = outer();
myNewFunction();
myNewFunction();
```


## Coding Exercises and My solutuon

### [Exercise 1:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
Write a closure named createCounter that takes an initial value start and returns a function. The returned function, when invoked, should increment the counter by 1 and return the updated value.

```javascript
const squareList = arr => {
  const arr1= arr.filter(num => num > 0 && num % parseInt(num) === 0)
          .map(num => Math.pow(num, 2));
  return arr1

};

const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
console.log(squaredIntegers);
```

### [Exercise 2:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
Write a closure named calculateAverage that takes an array of numbers, nums, and returns a function. The returned function, when invoked, should calculate and return the average of the numbers in the array.

```javascript
function calculateAverage(ArrayOfNumber){
   
  function innerAverage (){ 
    let sum =0
    for(let i=0;i<ArrayOfNumber.length;i++){
      sum=sum+ArrayOfNumber[i];
    }
    let result=sum/ArrayOfNumber.length;
    return result;
   }
  return innerAverage;
 }
 const myNewFunction = calculateAverage([1,2,3,4,5,6,7,8,9,10]);
 const result=myNewFunction();
 console.log(result);
```

### [Exercise 3:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
Write a closure named powerOf that takes a base number base and returns a function. The returned function, when invoked with an exponent exp, should calculate and return the result of base raised to the power of exp.

```javascript
function powerOf(baseNumber){
   
  function exponent (exp){ 
    return Math.pow(baseNumber,exp)
   }
  return exponent;
 }
 const myNewFunction = powerOf(2);
 const result=myNewFunction(5);
 console.log(result);
```

### [Exercise 4:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
Write a closure named compose that takes multiple functions as arguments and returns a new function. The returned function should apply the provided functions in reverse order, passing the result of each function as an argument to the next function.
```javascript
function add10(x) {
  return x + 10;
}

function multiply2(x) {
  return x * 2;
}

function subtract3(x) {
  return x - 3;
}

function compose(...functions) {
  return function(arg) {
    for (let i = functions.length - 1; i >= 0; i--) {
      arg = functions[i](arg);
    }
    return arg;
  };
}

const composedFunction = compose(subtract3, multiply2, add10);
console.log(composedFunction(10));
```
