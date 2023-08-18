# Day 6: 

This README file summarizes Data Fetch & Promises, Destructing Data, Async, Modules, and Wrapping up. 

## Lesson Summary

###  Data Fetch:
> * **URLs** point to resources on the web.
> * **APIs (Application Programming Interface)** services that are exposing a whole bunch of data at acertin URLs, provide URLs that point at data we care about.
The way that let us load data fron API in JS is by using the bulit in function fetch()
- fetch("https://dog.ceo/api/breed/hound/list")
->But if we run it in the console, we will see something weird ..
```javaScript
Promise {<pending>}
  [[Prototype]]: Promise
  [[PromiseState]]: "pending"
  [[PromiseResult]]: undefined
```
->Because it takes time to fetch data from the network, And that lead u to Promises 👇

###  Promise: 
Promises are used to handle asynchronous operations ( when we work with operations that take along time like fetch) in JavaScript.
**represent a value that we don’t have yet**.

#### Promises can be in 3 possible states:
1. `pending`: still waiting for the value, hang tight
2. `fulfilled` (aka `resolved`): finally got the value, all done (success)
3. `rejected`: sorry couldn't get the value, all done
   
It takes time for Promises to resolve, so they are **"asynchronous"**.


#### Using `await` keyword with Promises: 
`await` lets us tell JS to stop and wait for an asynchronous operation to finish.

In the case of a Promise, it waits for it to resolve before continuing with our code.

```javaScript
let response = await fetch("https://dog.ceo/api/breed/hound/list");
console.log(response);
```
- The Promise we get from `fetch()` resolves to a ***Response object***.
- body will contains the data we care about, but we need a way to reed this data 

#### `.json()`
Calling the `.json()` method on the response parses its body as a JSON object 
- It's body contains the data we care about, But that gives us another Promise cuz it's an **async** function.
To fix that we used `await`:

```javaScript
// Calling the .json() method on the response parses its body as a JSON object
let response = await fetch("https://dog.ceo/api/breed/hound/list");
let body = await response.json();
```

### Destructuring Data 
Destructuring is a fancy way of declaring multiple variables at once, by "extracting" values from an object with their property names.

```javaScript
const spices = [{name:"Waleed", nickname:"AbuKhalid"}]
// name = spices[0].name;
// nickname = spices[0].nickname;
let {name, nickname} = spices[0]; //name= Waleed, nickname= AbuKhalid 
let {nickname, name} = spices[0]; //nickname= AbuKhalid, name= Waleed 
```
> ordering is NOT important when destructuring object


#### Destructuring Data with array 

```javaScript
const [one, tow] = [1, 2] //one=1, tow=2
const [one, tow,three] = [1, 2] //one=1, tow=2, three=undefined

// We can ignore the values in the array we don't need
const [a, b] = [1, 2, 3, 4, 5] //a=1, b=2

// We can use commas to "Skip" values
const [,,a,,c] = [1, 2, 3, 4, 5] // a=3, c=5

// We can use ... to collect remaining values
 const [babySpice, ...adultSpices] = spices;
```
> ordering is important when destructuring arrays

#### `async` keyword
If we try to `await` something in a *regular function*, ***JS doesn't allow it*** because function is 'sync' and we have to write an `async` keyword before function.
```javaScript
async function getData(){
  let response = await fetch("https://dog.ceo/api/breed/hound/list");
  return response;
}

await getData()
```

- `createElement()` 
In an HTML document, the document`.createElement()` method creates the HTML element specified by tagName

```javaScript
const button = document.createElement("button")
```

- `appendChild()` 
The`.appendChild()` method of the Node interface adds a node to the end of the list of children of a specified parent node.

```javaScript
options.appendChild(button)
```

### Module 
Modules let us split big codebases across multiple files to let it easier work with them 
> To use the keyword 'await' out of script, while define the script tag we should adding the type="module", <script type='module'>

#### Module scope:
It's the sceond point of the differnce 'first one is await'. We can't access variables and functions in the web console since modules create their own space 

> And in this case we should use import & export
```javaScript
// mymodule.js
const a = () => "Waleed" 
export {a}
```
```javaScript
// othermodule.js
import {a} from './mymodule.js' 
```

### Debugging: 
We can `console.log()` or `console.warn()` or `console.error()` is one way to understand what's happening when your program runs

```javaScript
function whyIsntThisWorking(input) {
    console.log("Well at least we got this far");
    console.log(input);
    return thingThatDoesntWork(input);
}
```

* We can also use the browser's debugger to pause JS and inspect what's happening, The `debugger` statement creates a *breakpoint* where JS will pause and let you look around:

```javaScript
function whyIsntThisWorking(input) {
    debugger;
    return thingThatDoesntWork(input);
}
```
   
### `try` & `catch` Error Handling
`try` lets us "watch out" for potential errors, its friend `catch` lets us manage errors when they occur
```javaScript
try {
    thisMightThrowAnError();
} catch (error) {
    console.error("As if! Error:", error); 
    console.log("Whatever, let's press on anyway");
}
console.log("still rollin' with the homies");
```

### 💡 **Notes:**
1. **`trim()`** method removes whitespace from both ends of a string and returns a new string, without modifying the original string.
2. In `JS` we can create any element we want to appear in HTML page.


## Coding Exercise and my Solution:

[Task Discription](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week1%20-%20javascript-from-first-steps-to-professional/day%206/task.md)

[**My Solution**](https://github.com/WaleedZriqui/rick-MortyStarter.git)

<img src="images\Day6 task.png">