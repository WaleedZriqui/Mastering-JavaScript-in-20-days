# Day 5: 

This README file summarizes Conditionals, loops, and Map & filter. 

## Lesson Summary

### Conditionals
- If statement let us execute code under a certain condition (code in the if block only Runs if the condition is true )
- We can use else to run other code if (condition) is false.
- We can chain else and if blocks to account for multiple conditions.
- The condition is usually an expression that evaluate to a boolean if its given some other value JavaScript will convert it to a boolean
   - if("false") // true nonempty strings are truthy
   - if(0) //false
   - if(undefined) //false
   - if(null) //false
   - if("") //false (because it's immutable)
   - if([]) //true  objects are truthy
- Boolean logical operator:
   - The ! operator negates a boolean (!true=false)
   - The && we care about truthiness of more than one value (will be true only if both values are true) 
   - The || requires only one value to be truthy 
- Conditional ternary operator ( JavaScript has a shortcut operator for writing quick conditionals if we need 3 values to work).
   - let x = condition ? valueIfTrue : valueIfFalse 

### Loops
Loops let us run the same chunk of code multiple times
   - For loop 
   ```javascript
    for(let count=0; count<10; count++){ 
    console.log(count)}
    ```
   - while(condition){chunk of code} // let us run code over and over if condition is true
   - for ...of iterable loop: let us more easily iterate over items in a collection ,and we can use it to  iterate over characters in a string
      - With String   
      ```javascript
      for (let char of "ALOHA"){
      console.log(char)}
      ```
      - With array 
      ```javascript
      const numbers = [1,2,3]
      for(let n of numbers){ 
      console.log(n)}
      ```

### Map & filter
- maps and filter : methods let us process all the items in the array
> They are not mutate the array, only take a copy 
- Map calls a function on each item in an array to create a new array 
```javascript
const spices = [
  {name:"Emma", nickname: "Baby"}, 
  {name:"Geri", nickname: "Ginger"}
];
const nicknames = spices.map(s => s.nickname + " Spices"); // Output: ["Baby Spices", "Ginger Spices"]
// Or u can use backtickes (String template) above s => `${s.nickname} Spices`
```
- Filter calls a true\false function and creates a new array with only the items where the function return true 
```javascript
const mels = spices.filter(s => s.name.include("ma")); // Output: [{name:"Emma", nickname: "Baby"}]
```
- Reduce used to cmobine every items in one array 
- Spread we can use it to put all the items from one array inside another array
```javascript
const oldBurns = ["sqquare", "wack"]
const newBurns = ["basic", "dusty", "sus"]
const burnBook = [...oldBurns, ...newBurns] // Output: ["sqquare", "wack", "basic", "dusty", "sus"]
// is same as oldBurns.concat(newBurns)
```
```javascript
const skills = ["HTML", "CSS", "JS"]
const newSkills = ["React", "TypesScript", "Node"]
skills.push(...newSkills) // Output: ["HTML", "CSS", "JS", "React", "TypesScript", "Node"]
console.log(...skills) // Output: HTML CSS JS React TypesScript Node
```
- JavaScript can only do one task at a time ("single-threaded").
- When we give JavaScript a task that takes a while it doesnot stop and wait it adds the slow task to a TODO list and keeps on running our program the task runs sometimes later (Async) 
> Synchronus: Same time 
> Asynchronously: Not same time 
- The setTimeout() method executes a block of code after the specified time. setTimeout(function , time in milliseconds) 
```javascript
console.log("Print first")
setTimeout(()=>console.log("Print third"),1000)
console.log("Print second")

// Print first 
// Print second 
// after i sec=> Privt third
```

somethings take time:
   - waiting for user events.
   - asking a user to pick a file.
   - getting permission access camera/mic.
   - loading data from the interwebs .


## Coding Exercises and my Solution:

1. [Use Multiple Conditional (Ternary) Operators](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-multiple-conditional-ternary-operators)

```javascript
function checkSign(num) {
 return (num === 0) ? "zero" : (num>0) ? "positive" : "negative";
}
```

2. [Use the map Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-map-method-to-extract-data-from-an-array)

```javascript
const ratings = watchList.map((item)=>{
  return {title:item.Title, rating:item.imdbRating}
})
```

3. [Use the filter Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-filter-method-to-extract-data-from-an-array)

```javascript
const ratings = watchList.filter(s => parseFloat (s.imdbRating) >= 8.0)
const filteredList = ratings.map((item)=>{
  return {title:item.Title, rating:item.imdbRating}
});
```

4. [Golf Code](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/golf-code)

```javascript
const names = ["Hole-in-one!", "Eagle", "Birdie", "Par", "Bogey", "Double Bogey", "Go Home!"];

function golfScore(par, strokes) {
  if(strokes==1){
   return names[0];
  }else if(strokes<=par-2){
   return names[1];
  }else if(strokes===par-1){
    return names[2];
  }else if (strokes===par){
    return names[3];
  }else if(strokes<=par+1){
    return names[4];
  }else if(strokes===par+2){
    return names[5];
  }else if (strokes>=par+3){
    return names[6];
  }
  return "Change Me";
}
golfScore(5, 4);
```