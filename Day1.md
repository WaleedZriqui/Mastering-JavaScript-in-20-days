# Day 1:


This README file summarizes a general knowledge about JavaScript (What, Why, How). Also what we mean by DOM.


## Lesson Summary

### JavaScript
#### What is Javasceipt? 
It is a dynamic programming language of the web. 
#### Why is Javasceipt? 
Modify the websites and making them interactive
#### Where write Javascript?
1. The browser's console 
2. IDE, ex: VS Code, webstrom, ...
3. Online playground, ex: CodePen, CodeSandbox, ...


###Dom
#### What does DOM stand for?
Document Object Model => Separates a context of the document to the tree have a root element and extends to other element and so on

## Coding Examples

```javascript
document.body.children // Output: get all children elemnets inside the element Body 

document.getElementById("waleed") // Output: get first element with id = 'waleed' 
// Another way to use CSS selector with using # to represnt id 
document.querySelector("#waleed") // Output: get first element with id = 'waleed' 
document.querySelectorAll(".waleed") // Output: get all elements with class = 'waleed'
document.getElementById("waleed").textContnent // Output: return text inside the id 'waleed'
```


## Coding Exercises

- [Compound Assignment With Augmented Multiplication](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-multiplication)
- [Concatenating Strings with the Plus Equals Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-the-plus-equals-operator)
- [Use Bracket Notation to Find the Nth-to-Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-to-last-character-in-a-string)

### My Solution

```javascript
// Exercise 1: Augmented Multiplication
a *= 5; // a = a * 5  
b *= 3; // b = b * 3
c *= 10; // c = c * 10

// Exercise 2: Concatenating Strings
let myStr = 'This is the first sentence.';
myStr += ' This is the second sentence.' // Output: This is the first sentence. This is the second sentence.

// Exercise 3: Find the Nth-to-Last Character in a String
const lastName = "Lovelace";
const secondToLastLetterOfLastName = lastName[lastName.length - 2];

```

### At least
> Remeber that u don't need to remember all of that 🤔🤔
> U can use the [MDN](https://developer.mozilla.org/en-US/)
