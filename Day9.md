# Day 9: 

This README file summarizes the JavaScript lesson on Async JavaScript and Promises.

## Lesson Summary


### Async JavaScript 

#### JS is: 
- Single threaded language  (one command runs at a time)
- Synchronously executed (each line should be finished before move to another line)

So here what we should do if we need time to excute a line of JS? 
A one of answer we can use the bulit in function setTimeOut(), but there is an issue on it:
```javascript
function printHello(){
  console.log("Hello");
}
setTimeout(printHello,1000);
console.log("Me first!");
/* Output:
Me First
Hello (after 1 sec) 
*/ 
```
```javascript
function printHello(){
  console.log("Hello");
}
setTimeout(printHello,0);
console.log("Me first!");
/* Output:
Me First
Hello (without dellay) 
*/ 
```
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/38052a44-506f-40e8-b94f-ea7763069cc5)


=> So JavaScript is not enough - We need new pieces (some of which aren’t JavaScript at all)

#### Our core JavaScript engine has 3 main parts
* Thread of execution (execution context)
* Memory / variable environment
* callstack

#### What is difference between 'Synchronous Programming' and 'Asynchronous programming'?
- Synchronous programming is where the computer will complete one task before moving on to the next. (Do nat need time)
- Asynchronous programming in JavaScript handle tasks that may take some time to complete, such as fetching data from a server or reading a file. There are several ways to achieve asynchronous programming in JS callback functions, promises, and the newer async/await syntax.


We have rules for the execution of our asynchronously delayed code Hold promise-deferred functions in a microtask queue and callback function in a task queue (Callback queue) when the Web Browser Feature (API) finishes add the function to the Call stack (i.e. run the function) when:
- Call stack is empty & all global code run (Have the Event Loop check this condition). It's very important also to finish excute all global() code, so if the callstack() is empty but there are still rows in global() the queue will wait
- Prioritize functions in the microtask queue over the Callback queue
- Call stack
A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/4896591b-28dd-4291-a3e7-52c18180b8f0)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/63bd7449-1407-4319-b439-8dd9a8c81fd7)

> We look to the Queue when the stack is empty and all global() code are finished (Queue is for asynchronous) and this is the definition of **Event Loop**

#### Notes: 
1. JavaScript engin part of web browser.
2. JavaScript doesn't have the feature of a timer the browser provides the timer feature which JavaScript takes advantage of by using setTimeOut.
3. Some Javascript features are actually Browser APIs e.g (document , setTimeout , console , fetch ).
4. Functions that need to be asynchronously executed, are pushed onto the callback queue .
5. When the callstack is empty, the functions in the callback ( keep track of multiple function calls) queue are execute (when the event loop finds an empty call stack).
6. The callback function passed to the then() method is added to the microstack queue and when all global code is finished running and there's nothing on the callstack the event loop goes and checks the queues (first the microstack queue then callback queue)


### Promises 

* Special objects built into JavaScript that get returned immediately when we make a call to a web browser API/feature (e.g. fetch) that’s set up to return promises (not all are).
* A Promise is a JavaScript object that links producing ( takes some time ) code and consuming code (wait for a result).
* Promises act as a placeholder for the data we expect to get back from the web browser feature’s background work.
* Promises object has two propoties (value, onFulfilment[array]) 
* Value is passed to functions on onFulfilment while exceution using .then() 
* Promises are excuted like the same way we did for 'setTimeOut()' above 

```javaScript
function display(data){
    console.log(data)
}
const futureData = fetch('https://twitter.com/will/tweets/1')
futureData.then(display); 
 
console.log("Me first!");
```

A `promise object`, it's just an object *automatically created* in JavaScript by `fetch`.

It has 3 properties:
1. `Value` which is `undefined`.
2. `‘onFulfilment` which is an `empty array` - it's a hidden property.
2. `onRjection` which is an `empty array` - it's a hidden property.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/f36c527a-42b4-4329-b9c9-cb60ef356158)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/52967005-decf-434f-834b-8bc6fd7db4ef)


#### `.then` method and functionality to call on completion
* Any code we want to run on the returned data must also be saved on the promise object.
* Added using `.then` method to the hidden property `‘onFulfilment`.
* Promise objects will automatically trigger the attached function to run with its input being the returned data.


#### Web APIs & Promises Example:
```javaScript
function display(data){console.log(data)}
function printHello(){console.log("Hello");}
function blockFor300ms(){/* blocks js thread for 300ms*/ }

setTimeout(printHello, 0);

const futureData = fetch('https://twitter.com/will/tweets/1');
futureData.then(display);

blockFor300ms();
console.log("Me first!");
```

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/ff0c78f5-2877-408a-a665-9a9f4edc664b)

####  Order of execution: 
We have three things to organize the execution:
1. **call stack**.
2. **microtask queue**.
3. **callback queue**.
 
 
#### Promises review:
The promise object give us this amazing feature, that means if we get an error back - not the actual response object we want. It's not even gonna auto trigger any of your functions in `onFulfilment`, it's gonna trigger any functions that you stored in `onRejection`.

how do we get functions in `onRejection`?
there's two ways:
* Using `catch`: `futureData.catch(errfun)` >>> any function we pass in there, it's going `onRejection`.
* Using `.then`: `futureData.then(fun,errfun)` >>> the second argument fun is going to `onRejection`.

#### Note: 💡                       
> Any function i declear it as async, when I want to call it I should use .then() .catch() or use async/await.


## Coding Examples
```javascript
// Example 2: promises
let prom1 = new Promise((resolve, reject)=>{
	resolve("Success");
})
.then(e=>{console.log(e)})//Success
```

```javascript
// Example 3: promises
let prom1 = new Promise((resolve, reject)=>{
	reject("Error");
})
.then(e=>{console.log(e)}).catch(e=>{console.log(e)});//Error 
```


## Coding Exercise and my Solution:

### [Exercises for Async JS & Promises](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week2%20-%20javaScript-the-hard-parts-v2/day%203/tasks.md)

#### My Solution : Q1
```javascript


```

#### My Solution : Q2
```javascript
const apis = [
  {
    apiName: "products", 
    apiUrl: "https://dummyjson.com/products",
  }, 
  {
    apiName: "users", 
    apiUrl: "https://dummyjson.com/users",
  }, 
  {
    apiName: "posts", 
    apiUrl: "https://dummyjson.com/posts",
  }, 
  {
    apiName: "comments", 
    apiUrl: "https://dummyjson.com/comments",
  }
]
const  display =function(data){
 console.log(data);

}

function doWork(result, data) {
result.data=data;
  console.log(result);
}
const executeInParallelWithPromises = (apis) => {
apis.forEach((api)=>{
 const FutureData=fetch(api.apiUrl);
let result={name:api.apiName , URL:api.apiUrl}
 FutureData.then(data => data.json()).then(doWork.bind(null, result));
})
}
executeInParallelWithPromises(apis);
```
