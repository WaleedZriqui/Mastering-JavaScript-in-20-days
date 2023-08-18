# Day 9: 

This README file summarizes the JavaScript lesson on Async JavaScript and Promises.

## Lesson Summary

In this lesson, we explored Async JavaScript and Promises in JavaScript. Here are the key points covered:
- JavaScript is a single threaded language  (one command runs at a time)
- Synchronously executed (each line is run in order the code appear).
- Our core JavaScript engine has 3 main parts
   - Thread of execution
   - Memory / variable environment
   - callstack
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


## Coding Exercises

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