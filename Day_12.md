# Day 12

This README file summarizes the Philosophy of Coercion, Equality, and Static Typing 

## Lesson Summary

### Philosophy of Coercion
> JavaScript's dynamic typing isnot a weakness, it's one of itsstrong qualities

#### Exercise: Working With Coercion
In this exercise, you will define some validation functions that check user inputs (such as from DOM elements). You'll need to properly handle the coercions of the various value types. With these Instructions:

1. Define an `isValidName(..)` validator that takes one parameter, `name`. The validator returns `true` if all the following match the parameter (`false` otherwise):
	- must be a string
	- must be non-empty
	- must contain non-whitespace of at least 3 characters

2. Define an `hoursAttended(..)` validator that takes two parameters, `attended` and `length`. The validator returns `true` if all the following match the two parameters (`false` otherwise):
	- either parameter may only be a string or number
	- both parameters should be treated as numbers
	- both numbers must be 0 or higher
	- both numbers must be whole numbers
	- `attended` must be less than or equal to `length`

```javaScript
function isValidName(name) {
	if (
		typeof name == "string" &&
		name.trim().length >= 3
	) {
		return true;
	}

	return false;
}

function hoursAttended(attended,length) {
	if (
		typeof attended == "string" &&
		attended.trim() != ""
	) {
		attended = Number(attended);
	}
	if (
		typeof length == "string" &&
		length.trim() != ""
	) {
		length = Number(length);
	}
	if (
		typeof attended == "number" &&
		typeof length == "number" &&
		attended <= length &&
		attended >= 0 &&
		length >= 0 &&
		Number.isInteger(attended) &&
		Number.isInteger(length)
	) {
		return true;
	}

	return false;
}


// tests:
console.log(isValidName("Frank") === true);
console.log(hoursAttended(6,10) === true);
console.log(hoursAttended(6,"10") === true);
console.log(hoursAttended("6",10) === true);
console.log(hoursAttended("6","10") === true);

console.log(isValidName(false) === false);
console.log(isValidName(null) === false);
console.log(isValidName(undefined) === false);
console.log(isValidName("") === false);
console.log(isValidName("  \t\n") === false);
console.log(isValidName("X") === false);
console.log(hoursAttended("",6) === false);
console.log(hoursAttended(6,"") === false);
console.log(hoursAttended("","") === false);
console.log(hoursAttended("foo",6) === false);
console.log(hoursAttended(6,"foo") === false);
console.log(hoursAttended("foo","bar") === false);
console.log(hoursAttended(null,null) === false);
console.log(hoursAttended(null,undefined) === false);
console.log(hoursAttended(undefined,null) === false);
console.log(hoursAttended(undefined,undefined) === false);
console.log(hoursAttended(false,false) === false);
console.log(hoursAttended(false,true) === false);
console.log(hoursAttended(true,false) === false);
console.log(hoursAttended(true,true) === false);
console.log(hoursAttended(10,6) === false);
console.log(hoursAttended(10,"6") === false);
console.log(hoursAttended("10",6) === false);
console.log(hoursAttended("10","6") === false);
console.log(hoursAttended(6,10.1) === false);
console.log(hoursAttended(6.1,10) === false);
console.log(hoursAttended(6,"10.1") === false);
console.log(hoursAttended("6.1",10) === false);
console.log(hoursAttended("6.1","10.1") === false);
```


#### Equality  == Vs. ===

This is NOT true:
- `==` checks value (loose).
- `===` checks value and type (strict).

This is True:
- `==` allows coercion (when types are different).
- `===` disallows coercion (when types are the same).

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/79b9aba4-7ad2-4f41-8cfd-d60a641e6b0a)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/b9f7ac84-759e-4a5d-8dee-5d22e74428fd)


#### Coercive Equality

For the most part, you have the option of treating null and undefined as indistinguishable through coercive equality. Whether the property was ever created and has been reset back to null, or whether it's been reset back to undefined, or whether it was never created at all. Those are basically all the same condition, or at least I would argue, that's a better way to code, to treat those as indistinguishable.
As shown in pic below in the second code:

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/b5f491b8-5fd8-48b1-bfb9-0f90605fdbe7)


#### Double Equals Algorithm
If I had a triple equals and they were different types, it's always gonna fail. So I'm gonna have to make numbers. But if I know there can only be number or string, especially if one of them is definitely a number, then an exactly the same way as I allow this with the last things sign, several sides ago, why not also allow with the double equals, why not say that this code online for is more noisy unnecessarily so and the abstraction of the double equals it's helpful here.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/30f2144c-56a2-4c01-a66a-f8efc75bf440)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/380dcb8f-2c23-4dd3-8871-4f419b200ed1)

#### Double Equals Summary:

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/2a91f562-5e07-4dd6-9dad-5e5585d359be)


#### Double Equals Corner Cases

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/45b642b2-30c9-4274-980b-ca5a9d504f7a)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/c90742cd-4f76-41d3-9459-45e0595ecc53)

#### Double Equals Corner Cases: Booleans

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/a3ae5cc3-cd07-41f4-8b4f-c5cbe4437b45)


#### Corner Cases: Summary

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/6ee07543-427d-4d00-a32b-dff163e764c8)

#### The case for preferring Double Equals (==)
We should prefer the double equals in all possible places 

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/3e89a14f-4fa7-401c-8287-1241b4964337)


#### When we ***know*** the type(s) in a comparison:
* If both **types** are ***the same***, `==` is identical to `===`. Using `===` would be unnecessary, so prefer the shorter `==`.
* If the **types** are ***different***, using one `===` would be broken. Prefer the more powerful `==` or don't compare at all.
* If the **types** are ***different***, the equivalent of one `==` would be two (or more!) `===` (ie, "slower"). Prefer the "faster" single `==`.
* If the **types** are ***different***, two (or more!) `===` comparisons may distract the reader. Prefer the cleaner single `==`.

> ***Summary***: If u know the types whether the types match or not, `==` is the more sensible choice.

#### If you ***don't know*** the type(s) in a comparison:
* The uncertainty of not knowing types should be obvious to reader The most obvious signal is `===`.
* Not knowing the types is equivalent to assuming type conversion Because of corner cases, the only safe choice is `===`.

> ***Summary***: If you can't or won't use known and obvious types, `===` is the only reasonable choice.
> ***Summary***: Making types known and obvious leads to better code. If types are known, `==` is best.Otherwise, fall back to `===`.


#### Douple Equal Exercise (Wrangling Equality):
In this exercise, you will define a `findAll(..)` function that searches an array and returns an array with all coercive matches.

**Instructions**
1. The `findAll(..)` function takes a value and an array. It returns an array.
2. The coercive matching that is allowed:
	- exact matches (`Object.is(..)`), more details about [Object.is()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)
	- strings (except "" or whitespace-only) can match numbers
	- numbers (except `NaN` and `+/- Infinity`) can match strings (hint: watch out for `-0`!)
	- `null` can match `undefined`, and vice versa
	- booleans can only match booleans
	- objects only match the exact same object

```javaScript
function findAll(match,arr) {
  var ret = [];
  for (let v of arr) {
    if (Object.is(match,v)) {
      ret.push(v);
    }
    else if (match == null && v == null) { //null == undefine => true 
      ret.push(v);
    }
    else if (typeof match == "boolean") {
      if (match === v) {
        ret.push(v);
      }
    }
    else if (typeof match == "string" && match.trim() != "" && typeof v == "number" && !Object.is(v,-0)) {
      if (match == v) {
        ret.push(v);
      }
    }
    else if (typeof match == "number" && !Object.is(match,-0) && !Object.is(match,NaN) && !Object.is(match,Infinity) && !Object.is(match,-Infinity) && typeof v == "string" && v.trim() != "") {
      if (match == v) {
        ret.push(v);
      }
    }
  }
	return ret;
}

function setsMatch(arr1,arr2) {
	if (Array.isArray(arr1) && Array.isArray(arr2) && arr1.length == arr2.length) {
		for (let v of arr1) {
			if (!arr2.includes(v)) return false;
		}
		return true;
	}
	return false;
}

// tests:
var myObj = { a: 2 };

var values = [
	null, undefined, -0, 0, 13, 42, NaN, -Infinity, Infinity,
	"", "0", "42", "42hello", "true", "NaN", true, false, myObj
];

console.log(setsMatch(findAll(null,values),[null,undefined]) === true);
console.log(setsMatch(findAll(undefined,values),[null,undefined]) === true);
console.log(setsMatch(findAll(0,values),[0,"0"]) === true);
console.log(setsMatch(findAll(-0,values),[-0]) === true);
console.log(setsMatch(findAll(13,values),[13]) === true);
console.log(setsMatch(findAll(42,values),[42,"42"]) === true);
console.log(setsMatch(findAll(NaN,values),[NaN]) === true);
console.log(setsMatch(findAll(-Infinity,values),[-Infinity]) === true);
console.log(setsMatch(findAll(Infinity,values),[Infinity]) === true);
console.log(setsMatch(findAll("",values),[""]) === true);
console.log(setsMatch(findAll("0",values),[0,"0"]) === true);
console.log(setsMatch(findAll("42",values),[42,"42"]) === true);
console.log(setsMatch(findAll("42hello",values),["42hello"]) === true);
console.log(setsMatch(findAll("true",values),["true"]) === true);
console.log(setsMatch(findAll(true,values),[true]) === true);
console.log(setsMatch(findAll(false,values),[false]) === true);
console.log(setsMatch(findAll(myObj,values),[myObj]) === true);

console.log(setsMatch(findAll(null,values),[null,0]) === false);
console.log(setsMatch(findAll(undefined,values),[NaN,0]) === false);
console.log(setsMatch(findAll(0,values),[0,-0]) === false);
console.log(setsMatch(findAll(42,values),[42,"42hello"]) === false);
console.log(setsMatch(findAll(25,values),[25]) === false);
console.log(setsMatch(findAll(Infinity,values),[Infinity,-Infinity]) === false);
console.log(setsMatch(findAll("",values),["",0]) === false);
console.log(setsMatch(findAll("false",values),[false]) === false);
console.log(setsMatch(findAll(true,values),[true,"true"]) === false);
console.log(setsMatch(findAll(true,values),[true,1]) === false);
console.log(setsMatch(findAll(false,values),[false,0]) === false);
```

### TypeScript, Flow, and type-aware linting

📌 **Benefits:**  
1. Catch type-related mistakes
2. Communicate type intent
3. Provide IDE feedback
4. validating operand types to avoid errors

📌 **Caveats:**
1. Inferencing is best-guess, not a guarantee 
2. Annotations are optional 
3. Any part of the application that isn't typed introduces uncertainty

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/fb659e18-c9ab-4744-b8bc-5bf53ed2330c)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/100442bd-d4b0-41ce-8907-a1b709c9ec2e)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/f1344c21-388a-4445-b7b2-62fa9f83ab63)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/496e4fdb-d275-44eb-b632-f04d65f5dbc9)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/d5f0b69d-3edf-48e1-8d1d-09ad16e09c7c)



### Summary:
**[TypeScript vs Flow](https://github.com/niieani/typescript-vs-flowtype)** 


### TypeScript & Flow: Pros and Cons

📌 **Pros:**
* They make types more obvious in code.
* Familiarity: they look like other language's type systems.
* Extremely popular these days.
* They're very sophisticated and good at what they do.

📌 **Cons:**
* They use "non-JS-standard" syntax (or code comments).
* They require* a build process, which raises the barrier to entry.
* Their sophistication can be intimidating to those without prior formal types experience.
* They focus more on "static types" (variables, parameters, returns, properties, etc) than value types.
* The only way to have confidence over the runtime behavior is to limit/eliminate dynamic typing.



## Coding Exercise and my Solution:

### [QUESTION #1](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week3%20-%20deep-javascript-foundations-v3/day%202/tasks.md)
```javascript
const sayHelloWorld = new Promise(resolve, reject => {
  resolve("Hello world!");
});

const checkBoolean = (boolean) => new Promise(resolve, reject => {
  if (boolean) {
    resolve(boolean);
  } else {
    reject(`Input is false :(`)
  }
})

const returnObj = new Promise(resolve, reject => {
  resolve({
    x: "meow",
    y: 45,
  })
})

const promisesArray = [sayHeloWorld, checkBoolean, returnObj];

const convertToObj = (array) => {
  //write your code here;
  return obj;
}
```

### [QUESTION #2:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week3%20-%20deep-javascript-foundations-v3/day%202/tasks.md)
```javascript
function testScope1() {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
  console.log(a);
  console.log(b);
  console.log(c);
}

testScope1();

```
**Choices:**

A) `undefined`, `undefined`, `undefined`   
B) `1`, `undefined`, `ReferenceError`  
C) `1`, `ReferenceError`, `ReferenceError`   
D) `1`, `ReferenceError`

The correct choice is: **C**

* var has function scope, which means it's accessible throughout the function in which it's defined.
* let and const have block scope, which means they are only accessible within the block where they are defined.

Here's how the code behaves:

1. var a = 1; is declared within the if block, but due to the nature of var being function-scoped, it's accessible throughout the testScope1 function. Therefore, when console.log(a); is executed outside the if block, a still holds the value 1, and it will print 1.

2. let b = 2; is declared within the if block with block scope. This means it's not accessible outside the block in which it's defined. Therefore, when console.log(b); is executed outside the if block, b is out of scope, and a ReferenceError will occur, indicating that b is not defined.

3. const c = 3; is also declared within the if block with block scope. Like let, it's not accessible outside the block in which it's defined. When console.log(c); is executed outside the if block, c is out of scope, and a ReferenceError will occur, indicating that c is not defined.

### [QUESTION #3:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week3%20-%20deep-javascript-foundations-v3/day%202/tasks.md)
```javascript
function testScope2() {
  console.log(a);
  console.log(b);
  console.log(c);
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
}

testScope2();

```

**Choices:**

A) `undefined`, `ReferenceError`   
B) `1`, `undefined`, `ReferenceError`   
C)`undefined`, `undefined`,
`ReferenceError`  
D) `1`, `ReferenceError`

The correct choice is: **A**

1. console.log(a); is executed before the if block. Since var declarations are hoisted to the top of their containing function or global scope, the variable a is declared in the function scope and initialized to undefined at the beginning of the function. Therefore, console.log(a); will print undefined.

2. console.log(b); is executed before the if block. However, the variable b is declared with let inside the if block, and its scope is limited to that block. It's not accessible before its declaration, which results in a ReferenceError.

3. console.log(c); is also executed before the if block. Similar to let, the variable c is declared with const inside the if block, and its scope is limited to that block. Like let, it's not accessible before its declaration, resulting in a ReferenceError.

4. Inside the if block, var a = 1; declares a within the block scope. This declaration is hoisted to the top of the function, effectively overriding the previous declaration of a and initializing it with the value 1.

5. Inside the if block, let b = 2; declares b within the block scope. This declaration is not hoisted to the top of the function. Therefore, this b is a different variable from the one used outside the if block.

6. Inside the if block, const c = 3; declares c within the block scope. Like let, this declaration is not hoisted to the top of the function. This c is also a different variable from the one used outside the if block.


### [QUESTION #4:](https://github.com/orjwan-alrajaby/gsg-QA-Nablus-training-2023/blob/main/learning-sprint-1/week3%20-%20deep-javascript-foundations-v3/day%202/tasks.md)
```javascript
function testScope3() {
  var a = 36;
  let b = 100;
  const c = 45;

  console.log([a, b, c]);

  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;

    console.log([a, b, c]);
  }

  console.log([a, b, c]);
}

testScope3();

```

**choices:**

A) `[ 36, 100, 45 ]` | `[ 1, 2, 3 ]` | `[ 36, 2, 3 ]`   
B) `[ 36, 100, 45 ]` | `[1, 2, 3 ]` | `[ 36, 100, 45 ]`   
C) `[ 36, 100, 45 ]` | `[ 1, 2, 3 ]` | `[ 1,100, 45 ]`   
D) `[ 36, 100, 45 ]` | `[ 1, 2, 3 ]` | `[ 1, 2, 3 ]`


The correct choice is: **C**

1. At the beginning of the testScope3 function, var a = 36;, let b = 100;, and const c = 45; declare and initialize three variables: a with var, b with let, and c with const. These variables are function-scoped and are accessible within the entire function.

2. The first console.log([a, b, c]); logs the values of the initial declarations, which are [36, 100, 45].

3. Inside the if block:

    * var a = 1; reassigns the value of a to 1. This affects the previously declared a in the outer scope.
    * let b = 2; declares a new variable b with block scope. This does not affect the b declared in the outer scope.
    * const c = 3; declares a new variable c with block scope. This does not affect the c declared in the outer scope.
    * The second console.log([a, b, c]); logs the values within the if block, which are [1, 2, 3].
  
4. After the if block, the final console.log([a, b, c]); logs the values of the variables in the outer scope, where a has been reassigned to 1 within the if block, b is still 100, and c is still 45.
