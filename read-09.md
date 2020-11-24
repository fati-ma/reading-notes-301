# Readings: FunctionalL Programming
## Read:08 - Refactoring

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-09).

### For this class, I will be reading from these resource: `Functional Programming Concepts` and ` Refactoring Javascript for Readability` .

### :pushpin: [Functional Programming Concepts](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)
### :pushpin: [Refactoring Javascript for Readability](https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec)

## Article 1: Concepts of Functional Programming in Javascript

### What is functional programming?

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data 

### Pure functions

**It returns the same result if given the same arguments**

Imagine we want to implement a function that calculates the area of a circle. An impure function would receive radius as the parameter, and then calculate ```radius * radius * PI```:

```
let PI = 3.14;

const calculateArea = (radius) => radius * radius * PI;

calculateArea(10); // returns 314.0
```

Why is this an impure function? Simply because it **uses a global object** that was not passed as a parameter to the function.


**Reading Files**

If our function reads external files, it’s not a pure function — the file’s contents can change.

```
const charactersCounter = (text) => `Character count: ${text.length}`;

function analyzeFile(filename) {
  let fileContent = open(filename);
  return charactersCounter(fileContent);
}
```

**Random number generation**

Any function that relies on a random number generator cannot be pure.

```
function yearEndEvaluation() {
  if (Math.random() > 0.5) {
    return "You get a raise!";
  } else {
    return "Better luck next year!";
  }
}
```

**It does not cause any observable side effects**

Examples of observable side effects include modifying a global object or a parameter passed by reference.
Now we want to implement a function to receive an integer value and return the value increased by 1.

```
let counter = 1;

function increaseCounter(value) {
  counter = value + 1;
}

increaseCounter(counter);
console.log(counter); // 2
```

**Pure functions benefits**

The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:
   - Given a parameter A → expect the function to return value B
   - Given a parameter C → expect the function to return value D
   
A simple example would be a function to receive a collection of numbers and expect it to increment each element of this collection.
```
let list = [1, 2, 3, 4, 5];

const incrementNumbers = (list) => list.map(number => number + 1);
```

We receive the numbers array, use map incrementing each number, and return a new list of incremented numbers.
```
incrementNumbers(list); // [2, 3, 4, 5, 6]
```

For the input [1, 2, 3, 4, 5], the expected output would be [2, 3, 4, 5, 6].


### Immutability

Unchanging over time or unable to be changed.

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.


### Referential transparency

Basically, if a function consistently yields the same result for the same input, it is referentially transparent.

```
pure functions + immutable data = referential transparency
```


### Functions as first-class entities

The idea of functions as first-class entities is that functions are also treated as values and used as data.

Functions as first-class entities can:
   - refer to it from constants and variables
   - pass it as a parameter to other functions
   - return it as result from other functions
   
The idea is to treat functions as values and pass functions like data. This way we can combine different functions to create new functions with new behavior.


### Higher-order functions

When we talk about higher-order functions, we mean a function that either:
   - takes one or more functions as arguments, or
   - returns a function as its result
   
The doubleOperator function we implemented above is a higher-order function because it takes an operator function as an argument and uses it.

# ----------------------------------

## Article 2: Refactoring JavaScript for Performance and Readability

### Scenario 1

We're an URL-shortening website, like TinyURL. We accept a long URL and return a short URL that forwards visitors to the long URL. We have two functions.
```
// Unrefactored code

const URLstore = [];

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  URLstore.push({[rndName]: URL});
  return rndName;
}

function getLong(shortURL) {
  for (let i = 0; i < URLstore.length; i++) {
    if (URLstore[i].hasOwnProperty(shortURL) !== false) {
      return URLstore[i][shortURL];
    }
  }
}
```

`Problem`: what happens if getLong is called with a short URL that isn't in the store? Nothing is explicitly returned so undefined will be returned. Since we're not sure how we're going to handle that, let's be explicit and throw an error so that problems can be spotted during development.

`The answer is to use some form of hash function`, which Maps and Sets use under the surface. A hash function is used to map a given key to a location in the hash table. Below, this happens when we place our short URL into the store in makeShort and when we get it back out in getLong. Depending on how you're measuring run time, the result is that on average we only need to check one bucket — no matter how many total buckets there are!
```
// Refactored code

const URLstore = new Map(); // Change this to a Map

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  // Place the short URL into the Map as the key with the long URL as the value
  URLstore.set(rndName, URL);
  return rndName;
}

function getLong(shortURL) {
  // Leave the function early to avoid an unnecessary else statement
  if (URLstore.has(shortURL) === false) {
    throw 'Not in URLstore!';
  }
  return URLstore.get(shortURL); // Get the long URL out of the Map
  ```
  
  
### Scenario 2

We're a social media website where user URLs are generated randomly. Instead of random gibberish, we're going to use the friendly-words package that the Glitch team works on. They use this to generate the random names for your recently created projects!
```
// Unrefactored code

const friendlyWords = require('friendly-words');

function randomPredicate() {
  const choice = Math.floor(Math.random() * friendlyWords.predicates.length);
  return friendlyWords.predicates[choice];
}

function randomObject() {
  const choice = Math.floor(Math.random() * friendlyWords.objects.length);
  return friendlyWords.objects[choice];
}

async function createUser(email) {
  const user = { email: email };
  user.url = randomPredicate() + randomObject() + randomObject();
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
```
It's often said that a function should do one thing. Here, createUser does one thing .. kinda. It creates a user. However, if we're thinking ahead to the future, there's a good chance (if our business is successful) that this function is going to grow very large indeed.

Write `one function that accepts a list` of friendly things.
```
// Refactored code

const friendlyWords = require('friendly-words');

const generateURL = user => {
  const pick = arr => arr[Math.floor(Math.random() * arr.length)];
  user.url = `${pick(friendlyWords.predicates)}-${pick(friendlyWords.objects)}` +
    `-${pick(friendlyWords.objects)}`; // This line would've been too long for linters!
};

async function createUser(email) {
  const user = { email: email };
  // The URL-creation algorithm isn't important to this function so let's abstract it away
  generateURL(user);
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
```

