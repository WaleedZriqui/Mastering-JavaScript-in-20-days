# Day 5: 

This README file summarizes the JavaScript lesson on Conditionals, loops, and Map & filter. 

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
- When we give JavaScript a task that takes a while it doesnot stop and wait it adds the slow task to a TODO list and keeps on running our program the task runs sometimes later (Async) somethings take time:
   - waiting for user events.
   - asking a user to pick a file.
   - getting permission access camera/mic.
   - loading data from the interwebs .
- The setTimeout() method executes a block of code after the specified time. setTimeout(function , time in milliseconds) 


## Coding Examples
Example 1:
```html
<style>
.myStyle {
  background-color: coral;
  padding: 16px;
}
</style>
......
 const list = document.getElementById("myDIV").classList;
list.add("myStyle");//add the "myStyle" class to myDIV.
```
Example 2:
```javascript
let numbers=[1,2,5,6,7];
for(let num of numbers){
console.log(num); //1 2 5 6 7 
}
```
Example 3: Spread
```javascript
const oldArray1=[1,2,3];
const oldArray2=[4,5,6];


const newArray1= [...oldArray1,...oldArray2];
const newArray2=oldArray1.concat(oldArray2);


console.log(newArray1);//[ 1, 2, 3, 4, 5, 6 ]
//the same as 
console.log(newArray2);//[ 1, 2, 3, 4, 5, 6 ]

oldArray1.push(...oldArray2);
console.log(oldArray1);//[ 1, 2, 3, 4, 5, 6 ]

```

Example 4: setTimeout
```javascript

console.log("First");
setTimeout(()=> console.log("Third"),1000);// after 1 second 
console.log("Second");

//Result 
First

Second

Third 

```

## Coding Exercises

### [Use Multiple Conditional (Ternary) Operators](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-multiple-conditional-ternary-operators)

#### My Solution


```javascript
function checkSign(num) {
 return (num === 0) ? "zero" : (num>0) ? "positive" : "negative";

}

checkSign(10);

```
### [Use the map Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-map-method-to-extract-data-from-an-array)

#### My Solution


```javascript
// The global variable
const watchList = [
  {
    "Title": "Inception",
    "Year": "2010",
    "Rated": "PG-13",
    "Released": "16 Jul 2010",
    "Runtime": "148 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Christopher Nolan",
    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page, Tom Hardy",
    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
    "Language": "English, Japanese, French",
    "Country": "USA, UK",
    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.8",
    "imdbVotes": "1,446,708",
    "imdbID": "tt1375666",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Interstellar",
    "Year": "2014",
    "Rated": "PG-13",
    "Released": "07 Nov 2014",
    "Runtime": "169 min",
    "Genre": "Adventure, Drama, Sci-Fi",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan, Christopher Nolan",
    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
    "Language": "English",
    "Country": "USA, UK",
    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.6",
    "imdbVotes": "910,366",
    "imdbID": "tt0816692",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "The Dark Knight",
    "Year": "2008",
    "Rated": "PG-13",
    "Released": "18 Jul 2008",
    "Runtime": "152 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
    "Language": "English, Mandarin",
    "Country": "USA, UK",
    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
    "Metascore": "82",
    "imdbRating": "9.0",
    "imdbVotes": "1,652,832",
    "imdbID": "tt0468569",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Batman Begins",
    "Year": "2005",
    "Rated": "PG-13",
    "Released": "15 Jun 2005",
    "Runtime": "140 min",
    "Genre": "Action, Adventure",
    "Director": "Christopher Nolan",
    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
    "Language": "English, Urdu, Mandarin",
    "Country": "USA, UK",
    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
    "Metascore": "70",
    "imdbRating": "8.3",
    "imdbVotes": "972,584",
    "imdbID": "tt0372784",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Avatar",
    "Year": "2009",
    "Rated": "PG-13",
    "Released": "18 Dec 2009",
    "Runtime": "162 min",
    "Genre": "Action, Adventure, Fantasy",
    "Director": "James Cameron",
    "Writer": "James Cameron",
    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
    "Language": "English, Spanish",
    "Country": "USA, UK",
    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
    "Metascore": "83",
    "imdbRating": "7.9",
    "imdbVotes": "876,575",
    "imdbID": "tt0499549",
    "Type": "movie",
    "Response": "True"
  }
];

// Only change code below this line

// const ratings = [];
// for (let i = 0; i < watchList.length; i++) {
//   ratings.push({title: watchList[i]["Title"], rating: watchList[i]["imdbRating"]});
// }
const ratings =watchList.map((item)=>{
  return {title:item["Title"] , rating:item["imdbRating"]}
});
// Only change code above this line

console.log(JSON.stringify(ratings));
```

### [Use the filter Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-filter-method-to-extract-data-from-an-array)

#### My Solution


```javascript
// The global variable
const watchList = [
  {
    "Title": "Inception",
    "Year": "2010",
    "Rated": "PG-13",
    "Released": "16 Jul 2010",
    "Runtime": "148 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Christopher Nolan",
    "Actors": "Leonardo DiCaprio, Joseph Gordon-Levitt, Elliot Page, Tom Hardy",
    "Plot": "A thief, who steals corporate secrets through use of dream-sharing technology, is given the inverse task of planting an idea into the mind of a CEO.",
    "Language": "English, Japanese, French",
    "Country": "USA, UK",
    "Awards": "Won 4 Oscars. Another 143 wins & 198 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.8",
    "imdbVotes": "1,446,708",
    "imdbID": "tt1375666",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Interstellar",
    "Year": "2014",
    "Rated": "PG-13",
    "Released": "07 Nov 2014",
    "Runtime": "169 min",
    "Genre": "Adventure, Drama, Sci-Fi",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan, Christopher Nolan",
    "Actors": "Ellen Burstyn, Matthew McConaughey, Mackenzie Foy, John Lithgow",
    "Plot": "A team of explorers travel through a wormhole in space in an attempt to ensure humanity's survival.",
    "Language": "English",
    "Country": "USA, UK",
    "Awards": "Won 1 Oscar. Another 39 wins & 132 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMjIxNTU4MzY4MF5BMl5BanBnXkFtZTgwMzM4ODI3MjE@._V1_SX300.jpg",
    "Metascore": "74",
    "imdbRating": "8.6",
    "imdbVotes": "910,366",
    "imdbID": "tt0816692",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "The Dark Knight",
    "Year": "2008",
    "Rated": "PG-13",
    "Released": "18 Jul 2008",
    "Runtime": "152 min",
    "Genre": "Action, Adventure, Crime",
    "Director": "Christopher Nolan",
    "Writer": "Jonathan Nolan (screenplay), Christopher Nolan (screenplay), Christopher Nolan (story), David S. Goyer (story), Bob Kane (characters)",
    "Actors": "Christian Bale, Heath Ledger, Aaron Eckhart, Michael Caine",
    "Plot": "When the menace known as the Joker wreaks havoc and chaos on the people of Gotham, the caped crusader must come to terms with one of the greatest psychological tests of his ability to fight injustice.",
    "Language": "English, Mandarin",
    "Country": "USA, UK",
    "Awards": "Won 2 Oscars. Another 146 wins & 142 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTMxNTMwODM0NF5BMl5BanBnXkFtZTcwODAyMTk2Mw@@._V1_SX300.jpg",
    "Metascore": "82",
    "imdbRating": "9.0",
    "imdbVotes": "1,652,832",
    "imdbID": "tt0468569",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Batman Begins",
    "Year": "2005",
    "Rated": "PG-13",
    "Released": "15 Jun 2005",
    "Runtime": "140 min",
    "Genre": "Action, Adventure",
    "Director": "Christopher Nolan",
    "Writer": "Bob Kane (characters), David S. Goyer (story), Christopher Nolan (screenplay), David S. Goyer (screenplay)",
    "Actors": "Christian Bale, Michael Caine, Liam Neeson, Katie Holmes",
    "Plot": "After training with his mentor, Batman begins his fight to free crime-ridden Gotham City from the corruption that Scarecrow and the League of Shadows have cast upon it.",
    "Language": "English, Urdu, Mandarin",
    "Country": "USA, UK",
    "Awards": "Nominated for 1 Oscar. Another 15 wins & 66 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BNTM3OTc0MzM2OV5BMl5BanBnXkFtZTYwNzUwMTI3._V1_SX300.jpg",
    "Metascore": "70",
    "imdbRating": "8.3",
    "imdbVotes": "972,584",
    "imdbID": "tt0372784",
    "Type": "movie",
    "Response": "True"
  },
  {
    "Title": "Avatar",
    "Year": "2009",
    "Rated": "PG-13",
    "Released": "18 Dec 2009",
    "Runtime": "162 min",
    "Genre": "Action, Adventure, Fantasy",
    "Director": "James Cameron",
    "Writer": "James Cameron",
    "Actors": "Sam Worthington, Zoe Saldana, Sigourney Weaver, Stephen Lang",
    "Plot": "A paraplegic marine dispatched to the moon Pandora on a unique mission becomes torn between following his orders and protecting the world he feels is his home.",
    "Language": "English, Spanish",
    "Country": "USA, UK",
    "Awards": "Won 3 Oscars. Another 80 wins & 121 nominations.",
    "Poster": "http://ia.media-imdb.com/images/M/MV5BMTYwOTEwNjAzMl5BMl5BanBnXkFtZTcwODc5MTUwMw@@._V1_SX300.jpg",
    "Metascore": "83",
    "imdbRating": "7.9",
    "imdbVotes": "876,575",
    "imdbID": "tt0499549",
    "Type": "movie",
    "Response": "True"
  }
];

// Only change code below this line

const filteredList = watchList.map(item=>
{
  return {
    title:item["Title"],
    rating:item["imdbRating"]
    }
}).filter(item => {

  return parseFloat(item.rating)>=8;
}
);
// Only change code above this line

console.log(filteredList);

```

### [Golf Code](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/golf-code)

#### My Solution


```javascript
const names = ["Hole-in-one!", "Eagle", "Birdie", "Par", "Bogey", "Double Bogey", "Go Home!"];

function golfScore(par, strokes) {
  // Only change code below this line
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
  // Only change code above this line
}

golfScore(5, 4);

```