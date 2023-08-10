# Day 2:


This README file summarizes all of Values & Data Types.


## Lesson Summary

### Values & Data Types
#### What is value? 
Data we want to work withit
#### Who we can know type of this value? 
Using the bulit in operator (typeOf) which returns a string indicating the type of operators value 
```javascript 
typeOf "42" // Output: String 
``` 
#### What is the data types in JS?
1. Primitive Data Types
    - String 
    - Number
    - Boolean 
    - Undefined
    - Null 
    - ... 
2. Objects 
    - Object 
    - Array 
#### What is the difference between Undefined & Null?
- Undefined : It's type is undefined and we suppose have value but something go in wrong way like when u try to get value before defining it 
- Null : It's type is object and usually i want to set it with Null value 

### Strings 
#### ex: "FrontEnd Mastre", 'Gaza Sky Geeks', `Waleed Zriqui`
#### Methods: .toUpperCase(), .toLowerCase(), .indexOf(), .includes(), ...
> Note: We start searching in strings from index 0 

### Operators
- Arithmitic Operators: +, -, *, /, **, %, ++
- Comparison Operators: >, <, >=, <=
- Logical Operators: ||, &&
- Equality operators: ===, ==, !==, != 

#### What is the difference between === & ==?
#### (Strict Equal) ===: compare the value and type 
#### (Loosey Equal) ==: compare the value only  

### Variables 
- let: Declear a variable that only available inside the block where it's defined 
- var: Declear a variable that available in whole function   
- const: Declear and assigns a constant value for ever (can't be changed)

> JS doesn't care about type of variable when declering (Dynamic), if we need this we can use TypeScript 



## Coding Examples

```javascript
document.title.indexOf("W") // Output: return the first index for the char 'W' in the string  

document.title.includes("Waleed") // Output: return boolean if the string contains this substring or not 

document.querySelector("head h1").textContent.toUpperCase() // Output: Change the string in h1 to become capital letters 
//Also we can use CSS as HTML 
document.querySelector("head h1").style.textTransforamation = "uppercase" 

1 === 1 // Output: True 
1 === '1' // Output: False
1 == 1 // Output: True 
1 == '1' // Output: True
 
let a 
a // Output: undefined 

"ALOHA"[0];      // “A”
"ALOHA".length  // 5

"ALOHA".indexOf("L");   //1 
// What's the index of the first accourance of specific character
// if not exist will return -1

"ALOHA".includes("HA");  // true

"ALOHA".startsWith("AL"); // true
// Does this string start with some other string?

"ALOHA".indexOf("HA"); // 3
// At what index does this substring begin?

"ALOHA" + "!" // "ALOHA!";
 // Connecting strings together

"ALOHA".toLowerCase() // "aloha";
```


### Coding Exercises with my Solution

#### QUESTION #1

Consider the following JavaScript code, What will be the output of each console.log statement? **_You MUST explain WHY._**

```javascript
let a = 0;
let b = "0";
let c = false;
let d = "false";

console.log(a == b); // Output: true, the Loosey Equal (==) compare the equality of values only without types 
console.log(b === c); // Output: false, the strict Equal (===) compare the equality for both of values and types 
console.log(!!d); // Outpur: true, the var d is not empty string so it will be true value and !! will eliminates each others
```
-------------------------------------------------------------------

#### QUESTION #2:

Consider the following JavaScript expression:What will be the output of this expression? **_You MUST explain the steps of evaluation taken by JS_**.

```javascript
console.log(4 + 5 * "7");
```

- "7" is a string, and JS will convert the string to number in multiplication 
- 5 * 7 = 35 
- Adding the sum by 4 will max the result 39.

-------------------------------------------------------------------

#### QUESTION #3:

Evaluate the following expression:
What will be the output of this expression? **_You MUST explain the steps of evaluation taken by JS_**.

```javascript
let result = 5 + 2 * 3 - 1;
```
- Mulitplication operation: 2 * 3 is calculated => equals 6. 
- Addition operation: 6 + 5 is calculated => equal 11. 
- Subtraction operation: 11 - 1 is calculated => equals 10. 
- Assigning: The final result (10) is assigned to the variable result.

-------------------------------------------------------------------

#### QUESTION #4:

Consider the following code:
What will be the output of each `console.log` statement? **_You MUST explain WHY_**.

```javascript
let x = 10;
let y = '10';
console.log(x == y); // Output: true, the Loosey Equal (==) compare the equality of values only without types 
console.log(x === y); // Output: false, the strict Equal (===) compare the equality for both of values and types 
```

-------------------------------------------------------------------

#### QUESTION #5:

Given the code below:
What is the value of result? **_You MUST explain the steps of evaluation taken by JS_**

```javascript
let num = "15";
let isPositive = true;
let result = (num > 10 && isPositive) || num < 0;
console.log(result);
```

- Compare operation inside brackets: 15 > 10 => returns true 
- And Logical operation: true && true => returns true  
- Compare operation out brackets: 15 < 0 => returns false  
- OR logical operation: true || false => returns true  
- The Console will print => true 