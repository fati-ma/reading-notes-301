# PAIR PROGRAMMING
## Read: 02 - jQuery, Events, and The DOM 

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or this webpage markdown file using this [link](https://github.com/fati-ma/reading-notes-301/blob/main/read-02.md).

### For this class, I will be reading from these resources: `JavaScript and jQuery book by Jon Duckett` and `6 Reasons for Pair Programming` .

### :pushpin: JavaScript and jQuery book by Jon Duckett
### :pushpin: [6 Reasons for Pair Programming](https://www.codefellows.org/blog/6-reasons-for-pair-programming/)


## Book: JavaScript and jQuery book by Jon Duckett

### jQuery


It's a JavaScript file that is included in the web pages. 
It let's the developer find elements using CSS-style selectors and then do something with the elements using jQuery methods.

1. Find elements using css-style selectors.

```
$('li.hot')
```

2. Do something with the elements usong jQuery methods.

```
$('li.hot').addClass('complete');
```


### Why Use jQuery?

***jQuery doesn't do anything you cannot achieve with pure JavaScript.***
It is just a **JavaScript file** but estimates show it has been used on over a
quarter of the sites on the web, because **it makes coding simpler**.

**jQuery's motto** is >"Write less, do more," 

### A Matched Set/ jQuery Selection

When selecting one or more elements, a **jQuery Object** is returned.
It is also known as **matched set** or **jquery selection**.


![selector](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQT1WOLQcG-3BuR5VGVPtVPgWeBUZKYEreUdw&usqp=CAU)


### jQuery Methods That Get and Set Data

1. **Get Information**

```
var content = $('li').html();
```

2. **Set Information**

```
$('li').html('Updated');
```

### Looping

In plain JavaScript, if you wanted
to do the same thing to several
elements, you would need to
write code to loop through all of
the elements you selected.

With **jQuery**, *when a selector
returns multiple elements, you
can update all of them using the
one method*. There is no need to
use a loop

```
$('li em') .addClass('seasonal ') ;
$( 'li.hot') .addClass('favorite'); 
```

In this code, the same value is
added to the class attribute for
all of the elements that are found
using the selector. It doesn't
matter if there are one or many. 

The ability to update all of the
elements in the jQuery selection
is known as **implicit iteration**. 


### Changing

The process of placing several
methods in the same selector is
referred to as **chaining**. As you
can see, it results in code that is
far more compact. 

```
$( 'li[i d!="one"]').hide().delay(500). fadeln(1400); 
```

Most methods used to **update**
the jQuery selection can be
chained. However the methods
that **retrieve** information from
the DOM (or about the browser)
cannot be chained. 


### Checking a page is Ready to work with


jQuery's `.ready()` method checks that the page is ready for your code to work with.


![ready](data:image/png;base64,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)


**Shortcut for Ready event method on `document` object**

```
$(function() {
   //code..
});
```


### Getting Element Content

The `.html()` and `.text()` methods both retrieve and update the content of elements. 

**.html()**
When this method is used to retrieve information
from a jQuery selection, it retrieves only the HTML
inside the first element in the matched set, along
with any of its descendants. 


**.text()**
When this method is used to retrieve the text from
a jQuery selection, it returns the content from every
element in the jQuery selection, along with the text
from any descendants. 


## Updating Elements

- When the `.html()` and `.text()`
methods are used as setters (to
update content) they will replace
the content of each element in
the matched set (along with any
content and child elements).

- The `.replaceWith()` and
`.remove()` methods replace and
remove the elements they match
(as well as their content and any
child elements). 


### Inserting Elements

- `.before()`
This method inserts content
before the selected element(s)

- `.after()`
This method inserts content
after the selected element(s). 

- `.prepend()`
This method inserts content
inside the selected element(s),
after the opening tag. 

- `.append()`
This method inserts content
inside the selected element(s),
before the closing tag. 


### Getting and Setting Attribute Values

- `.attr() `
- `. removeAttr()`
- `. addCl ass()`
- `.removeClass()` 


### Getting & Setting CSS Properties

- `.css() method `

```
var backgroundColor = $( ' li ' ) . css( 'background-color' ); 
```

```
$('1 i ') .css({
' background- col or' : ' #272727' ,
' font-family' : 'Courier'
} ) ; 
```


### Event Methods

The `.on()` method is used to handle all events. 

| UI     | KEYBOARD | MOUSE     | FORM   | DOCUMENT |
|--------|----------|-----------|--------|----------|
| focus  | input    | click     | submit | ready    |
| blur   | keydown  | dblclick  | select | load     |
| change | keyup    | mouseup   | change | unload   |
|        | keypress | mousedown |        |          |
|        |          | mousemove |        |          |



### Loading jQuery From a CDN

```
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js">
</script>

<script>
window.jQuery || document.write('<script src=" js/jquery-1.10.2.js"><\/script>')
</script> 
```


## Article: 6 Reasons for Pair Programming


### How does pair programming work?

**Pair programming** commonly involves *two roles*: the **Driver** and the **Navigator**. The *Driver is the programmer who is typing and the only one whose hands are on the keyboard.* Handling the “mechanics” of coding, the Driver manages the text editor, switching files, version control, and—of course writing—code. The *Navigator uses their words to guide the Driver but does not provide any direct input to the computer*. The Navigator thinks about the big picture, what comes next, how an algorithm might be converted in to code, while scanning for typos or bugs. The Navigator might also utilize their computer as a second screen to look up solutions and documentation, but should not be writing any code.


### Why pair program?

Pair programming touches on all *four skills*: developers explain out loud what the code should do, listen to others’ guidance, read code that others have written, and write code themselves.

### The 6 reasons:

1. Greater efficiency.
Researches identified pairing enhances technical skills, team communication, and even enjoyability of coding in the workplace.

2. Engaged collaboration.
When two programmers focus on the same code, the experience is more engaging and both programmers are more focused than if they were working alone.

3. Learning from fellow students.
If one developer has a unique approach to a specific problem, pair programming exposes the other developer to a new solution.

4. Social skills.
Pair programming not only improves programming skills, but can also help programmers develop their interpersonal skills.

5. Job interview readiness.
The ability to work with and learn from others and stellar communication skills are as (or more!) important to a company than specific technical skills.

6. Work environment readiness.
Many companies that utilize pair programing expect to train fresh hires from CS-degree programs on how they operate to actually deliver a product.


