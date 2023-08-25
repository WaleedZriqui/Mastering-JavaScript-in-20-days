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
const result = generatedFunc(3); // Output: 6
//here generatedFunc() has a definition of function multiplyBy2() as a result of excution one time for createFunction()
```

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/8f7ccb83-e4a2-490f-9674-cf448e75ba89)

#### Notes: 💡
- We can declear variables and saved then inside running of another function. Not used there but instead returned them out 
- A closure is created when an inner function is returned from an outer function and still has access to its lexical scope, including the variables and parameters of the outer function.
- A closure is a function that preserves the outer scope in its inner scope.
- the Functions get a new memory every run/invocation
- When our functions get called, we create a live store of data (local memory/variable environment/state) for that function’s execution context.
- When the function finishes executing, its local memory is deleted (except the returned value)


Closures are powerful because they allow functions to retain access to the variables they need, even when they are invoked outside their original lexical scope. This behavior enables advanced patterns and techniques in JavaScript programming.


#### Calling a function in the same function call as it was defined
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

#### Calling a function outside of the function call in which it was defined
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
Here 👆 for the first time, we would think that this way will not work correctly way, because when we try to execute the function incrementCounter() we will not find the counter variable. But that's wrong because when we return the function we also return the whole local memory that exists (i.e. When a function is defined, it gets a bond to the surrounding Local Memory (“Variable Environment”) in which it has been defined) so it will work in correct way and this is known as a 'backpack'

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/f597a8a9-e03f-4574-9feb-86296d5a8abf)

> To access the variable 'counter' from myNewFunction we should use .Scope.counter 
> The ‘backpack’ (or ‘closure’) of live data is attached incrementCounter (then to myNewFunction) through a hidden property known as `[[scope]]` which persists when the inner function is returned out

#### What can we call this ‘backpack’?
- Closed over ‘Variable Environment’ (C.O.V.E.)
- Persistent Lexical Scope Referenced Data (P.L.S.R.D.)
- 'Backpack'
- 'Closure'

#### What happen if we run outer again?
```javascript
function outer (){
 let counter = 0;
 function incrementCounter (){ counter ++; }
 return incrementCounter;
}
const myNewFunction = outer();
myNewFunction(); // counter = 1
myNewFunction(); // counter = 2 

const anotherFunction = outer();
anotherFunction(); // counter = 1
anotherFunction(); // counter = 2

//Every one will got his backpack, is know as 'Individual backpacks'  
```

#### Clousers Applications:
- Helper functions: Everyday professional helper functions like ‘once’ and ‘memoize’ (used to make the function running only one time and memoization data to not rerun the funcation again if we already run it and have data)
- Asynchronous JavaScript: Callbacks and Promises rely on closure to persist state pin an asynchronous environment


## Coding Exercises and My solutuon

### [Question 1:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
```javascript
function createCounter (num){
 function incrementCounter (){ num ++; }
 return incrementCounter;
}
```

### [Question 2:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
```javascript
function calculateAverage (nums){
  function findAvg (){
    let avg = 0;
    for (let i of nums){
        avg += i
    }
    avg /= nums.length
    return avg
 }
 return findAvg;
}
```

### [Question 3:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
```javascript
function powerOf (base){
 function findPower (exp){ return Math.pow(base,exp)}
 return findPower;
}
```

### [Question 4:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%202/tasks.md)
```javascript
function compose (...functions){
    const reverse = functions.reverse()
    function newFunc (arg){
        for(let i = 0; i<reverse.length; i++){
            arg = reverse[i](arg)
        }
    }
    return newFunc()
}
```
