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
- Call stack is empty & all global code run (Have the Event Loop check this condition)
- Prioritize functions in the microtask queue over the Callback queue
- Call stack
A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/4896591b-28dd-4291-a3e7-52c18180b8f0)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/63bd7449-1407-4319-b439-8dd9a8c81fd7)



- JavaScript engin part of web browser.
- JavaScript doesn't have the feature of a timer the browser provides the timer feature which JavaScript takes advantage of by using setTimeOut.
- Some Javascript features are actually Browser APIs e.g (document , setTimeout , console , fetch ).
- Functions that need to be asynchronously executed, are pushed onto the callback queue .
- When the callstack is empty, the functions in the callback ( keep track of multiple function calls) queue are execute (when the event loop finds an empty call stack).

- A Promise is a JavaScript object that links producing ( takes some time ) code and consuming code (wait for a result).
- then(resolve , reject )
   - resolve : method is called whenever a promise is resolved It takes data from the resolved promise.
   - reject :  method is called whenever a promise is reject It takes data from the reject promise.
   - 
- When the timer expires, the callback function that was passed in the setTimeout() is placed to the callback queue (This is where your asynchronous code gets pushed to, and waits for the execution).
- The callback function passed to the then() method is added to the microstack queue and when all global code is finished running and there's nothing on the callstack the event loop goes and checks the queues (first the microstack queue then callback queue )


## Coding Examples

```javascript
// Example 1: setTimeout
function print(){
  console.log("After 0ms ");
}
setTimeout(print,0);
console.log("First");

/*
First 
After 0ms 
*/
```

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
