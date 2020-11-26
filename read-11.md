# Readings: EJS
## Read:11 - EJS

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-11).

### For this class, I will be reading from this resource: `EJS tutorial from WalkThroughCode on YouTube, Videos 1-5` .

### :pushpin: [EJS tutorial from WalkThroughCode](https://www.youtube.com/playlist?list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)

## Tutorial: EJS tutorial from WalkThroughCode

### How To Use EJS to Template Your Node Application

**Jade** comes as the view engine for Express by default but Jade syntax can be overly complex for many use cases. `EJS` *is one alternative does that job well and is very easy to set up*. Let’s take a look at how we can create a simple application and use EJS to include repeatable parts of our site (partials) and pass data to our views.


**Node Setup**


```
{
  "name": "node-ejs",
  "main": "server.js",
  "dependencies": {
    "ejs": "^3.1.5",
    "express": "^4.17.1"
  }
}
```

```
// load the things we need
var express = require('express');
var app = express();

// set the view engine to ejs
app.set('view engine', 'ejs');

// use res.render to load up an ejs view file

// index page
app.get('/', function(req, res) {
    res.render('pages/index');
});

// about page
app.get('/about', function(req, res) {
    res.render('pages/about');
});

app.listen(8080);
console.log('8080 is the magic port');
```


**Start Up our Server**

```
node server.js
```

Now we can see our application in the browser at ```http://localhost:8080 and http://localhost:3000/about```


### Create the EJS Partials

Like a lot of the applications we build, there will be a lot of code that is reused. We’ll call those **partials** and define three files we’ll use across all of our site: head.ejs, header.ejs, and footer.ejs.

views/partials/head.ejs
```
<meta charset="UTF-8">
<title>EJS Is Fun</title>

<!-- CSS (load bootstrap from a CDN) -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.5.2/css/bootstrap.min.css">
<style>
    body { padding-top:50px; }
</style>
```

views/partials/header.ejs
```
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="/">EJS Is Fun</a>
  <ul class="navbar-nav mr-auto">
    <li class="nav-item">
      <a class="nav-link" href="/">Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="/about">About</a>
    </li>
  </ul>
</nav>
```

views/partials/footer.ejs
```
<p class="text-center text-muted">© Copyright 2020 The Awesome People</p>
```


### Add the EJS Partials to Views

**Syntax for including an EJS Partial**

Use ```<%- include('RELATIVE/PATH/TO/FILE') %> to embed an EJS partial in another file.```

   - The hyphen <%- instead of just <% to tell EJS to render raw HTML.
   - The path to the partial is relative to the current file.
   
   
### Pass Data to Views and Partials

Go back into `server.js` file and add the following inside your `app.get('/')` route.

server.js
```
// index page
app.get('/', function(req, res) {
    var mascots = [
        { name: 'Sammy', organization: "DigitalOcean", birth_year: 2012},
        { name: 'Tux', organization: "Linux", birth_year: 1996},
        { name: 'Moby Dock', organization: "Docker", birth_year: 2013}
    ];
    var tagline = "No programming concept is complete without a cute animal mascot.";

    res.render('pages/index', {
        mascots: mascots,
        tagline: tagline
    });
});
```
We have created a **list** called mascots and a simple string called tagline.


**Render a Single Variable in EJS**

To echo a single variable, we just use ```<%= tagline %>```. Let’s add this to our index.ejs file:

views/pages/index.ejs
```
...
<h2>Variable</h2>
<p><%= tagline %></p>
...
```

