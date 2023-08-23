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
