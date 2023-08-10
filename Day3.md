# Day 3:

This README file summarizes all of Arrays and Objects. 

## Lesson Summary

### Arrays 
#### What is Arrays? 
Arrays help in keeping multiple values together in an orderd collection.

#### Examples:
```javaScript
let synonyms = ["plethora", "array", "cornucopia"]

synonyms.length // Output: 3, as the strings also arrays have a length
synonyms[1] // Output: "plethora"
synonyms.indexOf("cornucopia") // Output: 2, as the strings it starts from index 0
synonyms.includes("plethora") // Output: true, check if an array contains attached value
synonyms.includes("variety") // Output: false
synonyms[1] = "variety" // Output: synonyms = ["plethora", "variety", "cornucopia"] not as strings, we can modify the arrays
let lastItem = synonyms.pop() // Output: synonyms = ["plethora", "variety"], lastItem = "cornucopia" 
synonyms.push("multitude") // Output: synonyms = ["plethora", "variety", "multitude"]

let emptyArray = []
let oneItemArray = ["lonely"]
let mixedArray = ["pop", 6, "squish", false, document] // Arrays can contains differnets type for items
```

#### What is differnt between Arrays and Strings? 
- "GSG" == ["GSG"]      // Output: true
- "GSG" === ["GSG"]     // Output: false
- "GSG" === ["GSG"][0]  // Output: true

#### Array methods:
1. .sort()
2. .join()

```javaScript
["c","d","a","b"].sort() // Output: ["a","b,"c,"d"]
[100, 1, 10].sort() // Output: [1, 10, 100]
[100, 2 ,50].sort() // Output:[100, 2 ,50] because JS converts the elements into strings and then sorts them alphabetically (1< 2< 5)

["lions", "tigers", "bears oh!"].join(" & ") // Output: "lions & tigers & bears oh!", join the values in the array using the attached string 

[1, 2, 3].concat([4, 5, 6]); // Output: [1, 2, 3, 4, 5, 6] 

let a = [5, 6, 7]
a.push([8, 9, 10]) // Output: 4, .push() returns the new length to the array 
a; // Output: [5, 6, 7, [8, 9, 10]], nested arrays 
a[3] // Output: [8, 9, 10]
```
> Remember 🌟 MDN 🌟 is 🌟 our 🌟 friend 

### Mutability
In JS certian values behave differently than certian other values that we might think are similar

```javaScript
let abcArray = ["a", "b", "c"]
abcArray[1] = "d"
abcArray;  // Output: ['a', 'd', 'c']

let abcString = "abc"
abcString[1] = "d"
abcString; // Output: 'abc'
```

#### Whate is difference between Mutable vs. Immutable? 
* "Mutable" data can be edited (e.g. Arrays)
* "Immutable" data always stays the same (e.g. strings & other primitives)
 
#### Examples:
```javaScript
// Do these do the same thing?

let numbers1 = [1, 2, 3]
let result1 = numbers1.push(4) z
result1; // Output: [1, 2, 3, 4]
numbers1;  // Output: [1, 2, 3, 4]
 
let numbers2 = [1, 2, 3];
let result2 = numbers2.concat([4]);
result2; // Output: [1, 2, 3, 4] 
numbers2; // Output: [1, 2, 3], number2 isn't changed by concat()
```


#### Variables themselves can also be (im)mutable 

```javaScript
let letVariable = "original value";
letVariable = "new value";
letVariable; // Output: "new value"

const constVariable = "original value";
constVariable = "new Value";
constVariable; //Output: error, const var can't changed 
```


#### Immutable variable with mutable value 

What happens when we use `const` with a mutable value like an Array?
```javaScript
const operands = [4, 6];
const sum = operands[0] + operands[1]; //  10

operands[0] = 5; //Output: operands = [5, 6], since we change the vlaue inside array not the pointer to array 
const newSum = operands[0] + operands[1]; // 11
```


#### Variables & Arrays:

```javaScript
let array1 = [1,2,3]
let array2= array1
array1[1]=4

array1 // Output: [1,4,3]
array2 // Output: [1,4,3], since the 2 arrays are pointing to the same value

// Even if we used const nested of let then the result will be the same
```


### Objects 
* **Objects** collect multiple values together to describe more complex data (It's mutiple)
* **Objects** similar to how we can point at different values using variables in the code 
* **Objects** let us *point at* related values using *properties* in the object.

#### How u can got value of a value from Object? 
Using dot '.'

#### How u can add a new var with it's value inside object? 
By adding the equal assign in the right of dot char with the new name of vat (the same way of reassign a value)


```javaScript
// First Example:
const js = {
    name: "JavaScript",
    abbreviation: "JS",
    isAwesome: true,
    officialSpec: "ECMAScript",
    birthYear: 1995,
    creator: "Brendan Eich"
}
js.name; //Output: "JavaScript"
js.name.startsWith("Java"); //Output: true, startsWith is function for Strings 
let age = 2023 - js.birthYear; // Output: age = 27
js.learn = true; // add new property >> learn

// Second Example 
const indicisive = {
    lunch: "Sandwich",
}
indicisive.lunch; //Output: "Sandwich"
indicisive.lunch = "tacos"; 
indicisive.lunch; //Output: "tacos"
indicisive.snack = "Chips"
indicisive.lunch; //Output: "Chips"
```

#### How we can access a property in the Ojbect:
We can access a property in the object by using 2 ways:
1. Obj.nameOfVar
2. Obj["nameOfVar"]

> Note: We can't use indexes with Objects 

#### Methods with Object  
Properties can work with functions alsp
```javaScript
const dog = {
    name: "Ein",
    breed: "Corgi",
    speak: function () {
        console.log("woof woof");
    }
}
dog.speak(); //Output: "woof woof"
```

#### NOTES:💡
1. `this.` is a built-in object method.
2. We can have Nessted Objects 
3. We can have Array of Objects 
4. **push** will affect the original array while **concat** don’t, it creates a new array
5. **Objects** are mutable
6. **console** is a **built-in** **object** that has a property called **log**


## Coding Exercises and my Solution:

1. [Copy Array Items Using slice()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/copy-array-items-using-slice)
```javaScript
function forecast(arr) {
  return arr.slice(2,4);
}
console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
```

2. [Combine Arrays with the Spread Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/combine-arrays-with-the-spread-operator)
```javaScript
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun'];
  return sentence;
}

console.log(spreadOut());
```

3. [Profile Lookup](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/profile-lookup)
```javaScript
function lookUpProfile(name, prop) {
  for(let i=0; i<contacts.length; i++){
    if (name == contacts[i].firstName){
      if(contacts[i][prop] != undefined){
        return contacts[i][prop]
      }
      return "No such property"
    }
  }
  return "No such contact"
}

lookUpProfile("Akira", "likes");
```

4. [Write Reusable JavaScript with Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/write-reusable-javascript-with-functions)
```javaScript
function reusableFunction() {
  console.log("Hi World");
}
reusableFunction()
```

5. [Understanding Undefined Value returned from a Function](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/understanding-undefined-value-returned-from-a-function)
```javaScript
function addFive() {
  sum = sum + 5;
}
```

6. [Return a Value from a Function with Return](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-a-value-from-a-function-with-return)
```javaScript
function timesFive(num) {
  return num * 5;
}
```