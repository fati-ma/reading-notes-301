# Readings: The Call Stack
## Read:10 - The Call Stack and Debugging

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-10).

### For this class, I will be reading from these resource: `The Call Stack defined on MDN`, ` Understanding the JavaScript Call Stack` and `JavaScript error messages` .

### :pushpin: [The Call Stack defined on MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
### :pushpin: [Understanding the JavaScript Call Stack](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)
### :pushpin: [JavaScript error messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)

## Documentation: The Call Stack defined on MDN

A **call stack** is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple *functions* — what function is currently being run and what functions are called from within that function, etc.

  - When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.
  - Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.
  - When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.
  - If the stack takes up more space than it had assigned to it, it results in a "stack overflow" error.
  
**Example**
```
function greeting() {
   // [1] Some codes here
   sayHi();
   // [2] Some codes here
}
function sayHi() {
   return "Hi!";
}

// Invoke the `greeting` function
greeting();

// [3] Some codes here  
```

In summary, then, we start with an empty Call Stack. Whenever we invoke a function, it is automatically added to the Call Stack. Once the function has executed all of its code, it is automatically removed from the Call Stack. Ultimately, the Stack is empty again.


## Article: The JavaScript Call Stack - What It Is and Why It's Necessary

The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.

In Asynchronous JavaScript, we have a callback function, an event loop, and a task queue. The callback function is acted upon by the call stack during execution after the call back function has been pushed to the stack by the event loop.

**LIFO**: 
When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

**Temporarily store**: When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a `stack frame`. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.

![](https://cdn-media-1.freecodecamp.org/images/QgR2uIk7tW0YNz0Xm8g0jAPeRFI0e4sCejsv)

**What causes a stack overflow?**
A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

**In summary**
The key takeaways from the call stack are:
1. It is single-threaded. Meaning it can only do one thing at a time.
2. Code execution is synchronous.
3. A function invocation creates a stack frame that occupies a temporary memory.
4. It works as a LIFO — Last In, First Out data structure.


## Article: JavaScript error messages && debugging

This is a sample of an error, the green is the overall error message, the light blue is to note if the error was properly handled, the brownish (dark yellow) is the type of error and the red is the call stack

![](https://miro.medium.com/max/500/1*LHpmsxV3f2znpxhuAFuIqA.png)


### Types of error messages

**Reference errors**

This is as simple as when you try to use a variable that is not yet declared you get this type os errors.
```
console.log(foo) // Uncaught ReferenceError: foo is not defined
```

**Syntax errors**

This occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.
```
JSON.parse( {'foo': 'bar'} ) // Uncaught SyntaxError: Unexpected token o in JSON at position 1
```

**Range errors**

Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.
```
var foo= []
foo.length = foo.length -1 // Uncaught RangeError: Invalid array length
```

**Type errors**

Like the name indicates, this types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.
```
var foo = {}
foo.bar // undefined
foo.bar.baz // Uncaught TypeError: Cannot read property 'baz' of undefined
```

### Handling errors

About the light blue part of our earliest example of an error message, that shows up like that when we do not handle errors properly, meaning that anything after that error will not be executed. To avoid this we usually try to catch the errors so we can gracefully fallback to a default state of our application in case of an error (this fallback can be a 404 page which is normally not that graceful but is better than a page to just stop working).


