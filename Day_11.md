# Day 11 

This README file summarizes the Types and Coercion

## Lesson Summary

### Introduction 

```javaScript
let x = 2;
++x;  // 3 (i.e. this means x = x +1)

let y = "2";
++y; // should be 21 But it's 3 because in JS it's all time case to Number => Number (getValue)
```

### Types

* Primitive Types.
* Abstract Operations. 
* Coercion. 
* Equality. 
* TypeScript, Flow, etc.


> Everything inside JS is ***NOT*** an object >>> Everything ***can behave as*** an object.


#### Primitive Types:

- undefined.
- string.
- number.
- boolean.
- object.
- symbol: in ES6 used for auto private keys.
- bigInt (future): let x = 34n.

#### **NOTES**: 
* `functions` & `arrays` are a ***subtype*** of a *object type*.
* Those types are **NOT** objects:
    * undefined 
    * string 
    * number 
    * boolean 
    * symbol 
    * null 
    * bigint (future)

* Those types **ARE** objects:  
    * object
    * function 
    * array

* In JavaScript, `variables` ***don't*** have types,`values` ***do***.

#### NOTES: 
1. `typeof` operator always return string " ", ex:("undefined", "object", "string", ..)
2. function & arrays are not types of the top level they are subtypes of object, but when using `typeof array` = *object* while `typeof function` = *function*.
3. `typeof null` = *objec*t >>> it is a *bug* in JS.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/5d8eae1b-9ed0-46b2-94a7-5ca2aeeb93e6)

#### BigInt: 
var n = 42n 
Or 
BigInt(42)
typeof(v) // bigint

#### **undefined** vs. **undeclared** vs. **uninitialized (aka TDZ)** :
* `undefined`: We can have a variable that's been initialized that is undefined (doesn't hold a value at this moment)
* `undeclared`: We can have a variable that was never even created.
* `uninitialized`: We can have a variable that's never been initialized.

### NaN & isNaN:  
- NaN ("not a number") is Special Value and it is the only value that is ***not equal*** to itself (let say a is NAN, then a===a will return false)
- *Type of Nan*: NaN type is number (***invalid number***), becuase it cmoes from numeric operations
- isNan is a method that return if it's not number is a NAN or not 

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/3dc4b353-d45e-46b7-9ef4-eba4e7818bd9)


the isNaN utility coerces values to numbers before it checks for them to be NaN. So, it's gonna coerce the string `my son's age` to a number and guess what number it's gonna coerce it to? The NaN value, so of course it's gonna back true.
-> With ES6, we got a better utility, the `Number.isNan` utility. And that `Number.isNan` tells us defiantly for sure it's the NaN value or it's not. In other words ***it doesn't do any coercion*** for us.


### Negative Zero (another special value):

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/876b8f26-5b4e-46ca-b2e1-3b541bdf2bf3)

> Also (===) will fail in equality for -0 as NAN 
> `Object.is( , )` : it’s built-in checker, better way for checking equality (better than ===).

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/fa6f9a7d-7ae5-4f0c-ade7-810c1a58e538)


We might use -0 for directons in some applecaions which the sign means direction.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/29a7ce1d-d663-4c81-a5ee-5a11d92de855)




### Type Check Excersie
```javaScript
// TODO: define polyfill for `Object.is(..)`

if (!Object.is || true){   // to disaple the built in method & build my own
    Object.is = function ObjectIs(x,y){
        const xNegZero = isItNegZero(x)
        const yNegZero = isItNegZero(y)

        if (yNegZero || xNegZero ){
            return yNegZero && xNegZero
        }else if (isItNane(x) && isItNane(y)){
            return true
        }else {
            return x===y
        }

        function isItNegZero(v){
            return v===0 && (1/v)=== -Infinity
        }

        function isItNane(v){
            return v !==v
        }
    }
} 
```

#### Fundamental Objects
- aka: Built-In Objects.
- aka: Native Functions.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/98d6d3c4-2a21-4fcf-bdcf-5d5a8fd21ca6)


![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/7069c94e-980e-460e-9bf2-bfca446e6886)


### Coercion 
aka: ***type conversion***.

### Abstract Operations: **ToPrimitive**

#### ToString: `.toString()`
It takes any value and gives us the representation of that value in string form. And almost every value that you can imagine has at least some kind of representation in string form.

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/f872ef49-4579-424b-89eb-52bf2123d3ad)

```javaScript
String([]) // "" 
String([1,2,3]) // "1,2,3" 
String([null,undefined]) //"," 
String([[[],[],[]],[]]) //",,,"
String([,,,,]) // ",,,"
```

##### For the Object: we can override the toString() to return what we need as shown below. The useful thing here is JSON.strigfay()
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/882a3709-04dd-4d84-9964-bfa0a6500f04)

####  ToNumber: we can do it by `Number(x)` 
Anytime we need to do something numeric and we don't have a number, we're gonna invoke the ToNumber abstract operation
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/efc5151f-bf16-460e-a15b-61f5b3e04c7c)

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/2b38f8ae-1bb7-421d-a2de-7c9b7d5d401c)

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/94a8b349-baf5-4c20-ab57-ccc7faf92760)

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/06301a68-99ac-4c9a-acd0-9a0c639c85f3)


#### ToBoolean: we can do it by `Boolean(x)` and return if the value is `Falsy` or `Truthy`
Anytime you have any value that is not a Boolean, and it's used in a place that needs a Boolean, this operation occurs. Exactly the same as the other ones

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/4a8f3a7f-9439-4d99-aeb4-1a9dc53b8ac4)


### Cases of coercion: 

-> String Cases

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/8b33d69e-2d0c-4f48-a349-a9b15f226d8d)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/72831d46-600e-4b88-891f-095a6a268090)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/ffac7c01-4860-452d-9efa-e925c84df6f3)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/5153d1eb-4fab-47c7-9033-61195260e85c)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/e7c0df66-aaf0-4fd5-a755-1e838d64ab9b)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/4b76b170-eda8-4f68-bb46-a26afe1419cb)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/2e67ade4-b5f5-4961-ba83-5d4381828435)

-> Number Cases

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/8c415e02-09c7-4bd4-8fec-d248322e314e)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/e064521d-cc8b-4c74-8b18-922ee83e572f)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/839091e4-77b2-46b8-8eb1-9c0299b145e2)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/b319949d-0582-46d7-83f1-0f64d5272306)

-> Boolean Cases

![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/e4215841-dcad-4eda-8e76-b06f9499576e)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/8a8a8781-6a51-4681-b27d-9497a3602260)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/7178302c-9f59-42fe-841b-e4c4efd20500)
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/2dbe7b2a-18a3-4539-896d-7561fdd0c10f)


### Boxing
![image](https://github.com/WaleedZriqui/Mastering-JavaScript-in-20-days/assets/90526475/e25892db-4722-41cd-a786-b8796a1f25b6)

Remember, you access a length on a primitive string or some method on a primitive number, for example. So how does that work?
Boxing is a form of implicit coercion what helpful and go ahead and make the not an object to become an object to access all properties and methods on them (i.e. JavaScript implicitly coerces these primitives into their object)


### Conversion Corner Cases
It's ok to use boolean corresion with undefined and null but not ok with number and objects since there are many edge and corner cases 
![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/499ad77e-d128-4015-a797-99bea1c67e74)
![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/bef92dac-d976-4eff-99ce-b9f0babbe701)
![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/65aa3b55-1ad4-4855-912c-ede7167623dc)

## Coding Exercise and my Solution:
