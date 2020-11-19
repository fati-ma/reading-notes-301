# Readings: NODE.JS
## Read:06 - Node, Express, and APIs

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-06).

### For this class, I will be reading from this resource: `An Introduction to Node.js on sitepoint.com`.

### :pushpin: [An Introduction to Node.js on sitepoint.com](https://www.sitepoint.com/an-introduction-to-node-js/)


## Article: An Introduction to Node.js 


### What Is Node.js?

Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.


### How Do I Install Node.js?

1. You can check that Node is installed on your system by opening a terminal and typing `node -v`.

2. Next, create a new file `hello.js` and copy in the following code:
```
console.log("Hello, World!");
```

3. This uses Node’s **built-in console module** to display a message in a terminal window. To run the example, enter the following command:
```
node hello.js
```
If Node.js is configured properly, “Hello, World!” will be displayed.


### Installing a Package Globally

1. Open your terminal and type the following:
```
npm install -g jshint
```

2. This will install the jshint package globally on your system. We can use it to lint the `index.js` file from the previous example:
```
jshint index.js
```

You should now see a number of ES6-related errors. If you want to fix them up, add `/* jshint esversion: 6 */` to the top of the `index.js` file, re-run the command and linting should pass.


### Installing a Package Locally

We can also install packages locally to a project, as opposed to globally, on our system. 

1. Create a `test` folder and open a terminal in that directory. 

2. Next type this:
```
npm init -y
```

3. This will create and auto-populate a `package.json` file in the same folder. Next, use npm to install the lodash package and save it as a project dependency:
```
npm install lodash --save
```

4. Create a file named `test.js` and add the following:
```
const _ = require('lodash');

const arr = [0, 1, false, 2, '', 3];
console.log(_.compact(arr));
```

5. Finally, run the script using node `test.js.` You should see ```[ 1, 2, 3 ]``` output to the terminal.


### Working with the `package.json` File

If you look at the contents of the `test` directory, you’ll notice a folder entitled `node_modules`. This is where `npm` has saved lodash and any libraries that lodash depends on. The `node_modules` folder shouldn’t be checked in to version control, and can, in fact, be re-created at any time by running npm install from within the project’s root.

If you open the `package.json` file, you’ll see lodash listed under the dependencies field. By specifying your project’s dependencies in this way, you allow any developer anywhere to clone your project and use `npm` to install whatever packages it needs to run.


### The Node.js Execution Model


![img](https://uploads.sitepoint.com/wp-content/uploads/2012/10/1516152673node_event_loop.png)


### Are There Any Downsides?

1. Blocking I/O calls should be avoided, CPU-intensive operations should be handed off to a worker thread, and errors should always be handled correctly for fear of crashing the entire process.

2. Some developers also dislike the callback-based style of coding that JavaScript imposes (so much so that there’s even a site dedicated to the horrors of writing asynchronous JavaScript).


### “Hello, World!” — Server Version

Let’s have a quick look at a “Hello, World!” example HTTP server:

```
const http = require('http');

http.createServer((request, response) => {
  response.writeHead(200);
  response.end('Hello, World!');
}).listen(3000);

console.log('Server running on http://localhost:3000');
```

To run this, copy the code into a file named `hello-world-server.js` and run it using `node hello-world-server.js`. Open up a browser and navigate to ```http://localhost:3000``` to see “Hello, World!” displayed in the browser.


### What Are the Advantages of Node.js?

1. Aside from speed and scalability, an often-touted advantage of using JavaScript on a web server — as well as in the browser — is that your brain no longer needs to switch modes.
2. It speaks JSON. 
3. JavaScript is ubiquitous:This means that transitioning to Node development is potentially easier than to other server-side languages.

