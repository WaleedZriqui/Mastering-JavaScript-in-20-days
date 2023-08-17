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
const spices = [{name:"Aya", nickname:"Butterfly"}]
let {name, nickname} = spices[0]; //ordering is important when destructuring object
```

### Use it with array 

```javaScript
const [one, tow ] = [1,2] //ordering is important when destructuring arrays

// We can ignore the values in the array we don't need
const [,,melB] = spices;

// We can use ... to collect remaining values
 const [babySpice, ...adultSpices] = spices;
```
#### 💡**NOTE:**
> Order is important when destructuring arrays but not in objects.


## `async`

If we try to `await` something in a *regular function*, ***JS doesn't allow it*** >>> we have to write an `async` function.


### `createElement()` 
In an HTML document, the document`.createElement()` method creates the HTML element specified by tagName

```javaScript
const button = document.createElement("button")
```


### `appendChild()` 
The`.appendChild()` method of the Node interface adds a node to the end of the list of children of a specified parent node.

```javaScript
options.appendChild(button)
```

## Doggo Fetch Project
```javaScript
<!DOCTYPE html>
<html lang="en-US"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Doggo Fetch</title>
    <style>
        body {
            margin: 1rem auto;
            padding: 3rem;
            font-family: sans-serif;
        }
        header {
            width: 70%;
            margin: 1em auto;
        }
        main {
            max-width: 70%;
            margin: 0px auto;
            display:flex; 
            flex-direction: column;
        }
        img {
            max-width: 100%;
        }
        #image-frame {
            font-size: x-large;
            text-align: center;
            margin: 1rem auto;
        }
        #explanation, #score {
            padding: 1rem;
            text-align: center;
        }
        #options {
            max-width: 100%;
            display: flex;
            flex-direction: column;
        }
        button {
            padding: 0.5rem;
            font-size: medium;
            border-radius: 5px;
        }
        .correct {
            background-color: lightgreen;
        }
        .incorrect {
            background-color: lightpink;
        }
        .hidden {
            display: none;
        }
    </style>
  </head>
  <body>
    <header>
    <h1>Guess the Doggo</h1>
    <p>What breed is the dog in this image?</p>

    </header>

    <main>
    <div id="image-frame"><img src="./Final_files/PXL_20210220_100624962.jpg"></div>
    <div id="options">
    <button name="medium poodle" value="medium poodle" class="correct">medium poodle</button><button name="australian terrier" value="australian terrier" class="incorrect">australian terrier</button><button name="french bulldog" value="french bulldog">french bulldog</button></div>

    </main>

  


  <script type="module">

    const RANDOM_IMG_ENDPOINT = "https://dog.ceo/api/breeds/image/random";

    const BREEDS = ["affenpinscher", "african", "airedale", "akita", "appenzeller", "shepherd australian", "basenji", "beagle", "bluetick", "borzoi", "bouvier", "boxer", "brabancon", "briard", "norwegian buhund", "boston bulldog", "english bulldog", "french bulldog", "staffordshire bullterrier", "australian cattledog", "chihuahua", "chow", "clumber", "cockapoo", "border collie", "coonhound", "cardigan corgi", "cotondetulear", "dachshund", "dalmatian", "great dane", "scottish deerhound", "dhole", "dingo", "doberman", "norwegian elkhound", "entlebucher", "eskimo", "lapphund finnish", "bichon frise", "germanshepherd", "italian greyhound", "groenendael", "havanese", "afghan hound", "basset hound", "blood hound", "english hound", "ibizan hound", "plott hound", "walker hound", "husky", "keeshond", "kelpie", "komondor", "kuvasz", "labradoodle", "labrador", "leonberg", "lhasa", "malamute", "malinois", "maltese", "bull mastiff", "english mastiff", "tibetan mastiff", "mexicanhairless", "mix", "bernese mountain", "swiss mountain", "newfoundland", "otterhound", "caucasian ovcharka", "papillon", "pekinese", "pembroke", "miniature pinscher", "pitbull", "german pointer", "germanlonghair pointer", "pomeranian", "medium poodle", "miniature poodle", "standard poodle", "toy poodle", "pug", "puggle", "pyrenees", "redbone", "chesapeake retriever", "curly retriever", "flatcoated retriever", "golden retriever", "rhodesian ridgeback", "rottweiler", "saluki", "samoyed", "schipperke", "giant schnauzer", "miniature schnauzer", "english setter", "gordon setter", "irish setter", "sharpei", "english sheepdog", "shetland sheepdog", "shiba", "shihtzu", "blenheim spaniel", "brittany spaniel", "cocker spaniel", "irish spaniel", "japanese spaniel", "sussex spaniel", "welsh spaniel", "english springer", "stbernard", "american terrier", "australian terrier", "bedlington terrier", "border terrier", "cairn terrier", "dandie terrier", "fox terrier", "irish terrier", "kerryblue terrier", "lakeland terrier", "norfolk terrier", "norwich terrier", "patterdale terrier", "russell terrier", "scottish terrier", "sealyham terrier", "silky terrier", "tibetan terrier", "toy terrier", "welsh terrier", "westhighland terrier", "wheaten terrier", "yorkshire terrier", "tervuren", "vizsla", "spanish waterdog", "weimaraner", "whippet", "irish wolfhound"];

    
    // Utility function to get a randomly selected item from an array
    function getRandomElement(array) {
        const i = Math.floor(Math.random() * array.length);
        return array[i];
    }

    // Utility function to shuffle the order of items in an array in-place
    function shuffleArray(array) {
        return array.sort((a,b) => Math.random() - 0.5);
    }



    // TODO 1
    // Given an array of possible answers, a correct answer value, and a number of choices to get,
    // return a list of that many choices, including the correct answer and others from the array
    function getMultipleChoices(n, correctAnswer, array) {
        // Use a while loop and the getRandomElement() function
        // Make sure there are no duplicates in the array
        const choices = [correctAnswer];
        while (choices.length < n) {
            let candidate = getRandomElement(array);
            if (choices.indexOf(candidate) < 0) { // check if this is already in the array
                choices.push(candidate); // if not, add it
            }
        }
        return shuffleArray(choices);
    }

    
    // TODO 2
    // Given a URL such as "https://images.dog.ceo/breeds/poodle-standard/n02113799_2280.jpg"
    // return the breed name string as formatted in the breed list, e.g. "standard poodle"
    function getBreedFromURL(url) {
        // The string method .split(char) may come in handy
        // Try to use destructuring as much as you can
        const [,path] = url.split("/breeds/");
        const [breedID] = path.split("/");
        const [breed, subtype] = breedID.split("-");
        return [subtype, breed].join(" ");
    }



    // TODO 3
    // Given a URL, fetch the resource at that URL, 
    // then parse the response as a JSON object,
    // finally return the "message" property of its body
    async function fetchMessage(url) {
        const response = await fetch(url);  // Fetch the resource at the given URL
        const {message} = await response.json(); // Parse the response as JSON & remember its 'message' value
        return message; // Return the message
    }


    // Function to add the multiple-choice buttons to the page
    function renderButtons(choicesArray, correctAnswer) {

        // Event handler function to compare the clicked button's value to correctAnswer
        // and add "correct"/"incorrect" classes to the buttons as appropriate
        function buttonHandler(e) {
            if (e.target.value === correctAnswer) {
                e.target.classList.add("correct");
            } else {
                e.target.classList.add("incorrect");
                document.querySelector(`button[value="${correctAnswer}"]`).classList.add("correct");
            }
        }

        const options = document.getElementById("options"); // Container for the multiple-choice buttons

        // TODO 4
        // For each of the choices in choicesArray,
        // Create a button element whose name, value, and textContent properties are the value of that choice,
        // attach a "click" event listener with the buttonHandler function,
        // and append the button as a child of the options element
        choicesArray.map(choice => {
            let button = document.createElement("button");
            button.value = button.name = button.textContent = choice;
            button.addEventListener("click", buttonHandler);
            options.appendChild(button);
        })
    }


    // Function to add the quiz content to the page
    function renderQuiz(imgUrl, correctAnswer, choices) {
        const image = document.createElement("img");
        image.setAttribute("src", imgUrl);
        const frame = document.getElementById("image-frame");

        image.addEventListener("load", () => {
            // Wait until the image has finished loading before trying to add elements to the page
            frame.replaceChildren(image);
            renderButtons(choices, correctAnswer);
        })
        
    }

    // Function to load the data needed to display the quiz
    async function loadQuizData() {
        document.getElementById("image-frame").textContent = "Fetching doggo...";
        
        const doggoImgUrl = await fetchMessage(RANDOM_IMG_ENDPOINT);
        const correctBreed = getBreedFromURL(doggoImgUrl);
        const breedChoices = getMultipleChoices(3, correctBreed, BREEDS);

        return [doggoImgUrl, correctBreed, breedChoices];
    }

    // TODO 5
    // Asynchronously call the loadQuizData() function,     
    // Then call renderQuiz() with the returned imageUrl, correctAnswer, and choices 
    const [imageUrl, correctAnswer, choices] = await loadQuizData();
    renderQuiz(imageUrl, correctAnswer, choices);
    


  </script>

</body></html>
```


### Module scope:

> ### 💡 Note:
> We can't access variables and functions in the web console.


## Debugging: 
We can `console.log()` or `console.warn()` or `console.error()` is one way to understand what's happening when your program runs

```javaScript
function whyIsntThisWorking(input) {
    console.log("Well at least we got this far");
    console.log(input);
    return thingThatDoesntWork(input);
}
```

You can also use the browser's debugger to pause JS and inspect what's happening, The `debugger` statement creates a *breakpoint* where JS will pause and let you look around:

```javaScript
function whyIsntThisWorking(input) {
    debugger;
    return thingThatDoesntWork(input);
}
```


## 💡 **Notes:**
1. **`trim()`** method removes whitespace from both ends of a string and returns a new string, without modifying the original string.
2. In `JS` we can create any element we want to appear in HTML page.
   
### `try` `catch` Error Handling

`try` lets us "watch out" for potential errors, its friend `catch` lets us manage errors when they occur:

```javaScript
try {
    thisMightThrowAnError();
} catch (error) {
    console.error("As if! Error:", error); 
    console.log("Whatever, let's press on anyway");
}
console.log("still rollin' with the homies");
```



# Exercises🔥:

[Task Discription](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week1%20-%20javascript-from-first-steps-to-professional/day%206/task.md)

[**My Solution**](To be solved)