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

![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/de47f3d2-6cdf-4185-b03d-87298947f10d)


the isNaN utility coerces values to numbers before it checks for them to be NaN. So, it's gonna coerce the string `my son's age` to a number and guess what number it's gonna coerce it to? The NaN value, so of course it's gonna back true.
-> With ES6, we got a better utility, the `Number.isNan` utility. And that `Number.isNan` tells us defiantly for sure it's the NaN value or it's not. In other words ***it doesn't do any coercion*** for us.


### Negative Zero (another special value):

![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/e38c8178-4a82-4b9f-8b2c-1ce087665b1c)

> Also (===) will fail in equality for -0 as NAN 
> `Object.is( , )` : it’s built-in checker, better way for checking equality (better than ===).

![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/30133e50-283f-41b3-b4f7-567a868f5f21)


We might use -0 for directons in some applecaions which the sign means direction.

![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/155b7443-5484-490c-9e2d-4a4b08d1c33d)




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

![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/55a7346a-127e-4de8-9365-8c23295226ee)


![image](https://github.com/aya-thafer2/Mastering-JavaScript-in-20-Days/assets/121509832/b75233bf-b584-4923-bb6e-5b6296f5c6d1)
