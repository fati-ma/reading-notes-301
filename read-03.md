# MUSTACHE and FLEXBOX
## Read: 03 - Flexbox and Templating

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-03).

### For this class, I will be reading from these resources: `Templating with Mustache`, `A Guide to Flexbox` and `Flexbox Froggy` .

### :pushpin: [Templating with Mustache](https://medium.com/@1sherlynn/javascript-templating-language-and-engine-mustache-js-with-node-and-express-f4c2530e73b2)
### :pushpin: [A Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
### :pushpin: [Flexbox Froggy](https://flexboxfroggy.com/)


## Article 1: Templating with Mustache

### Javascript Templating

Javascript templating is a fast and efficient technique to render client-side view templates with Javascript by using a JSON data source. The template is HTML markup, with added templating tags that will either insert variables or run programming logic.
The template engine then replaces variables and instances declared in a template file with actual values at runtime, and convert the template into an HTML file sent to the client.


### Mustache


![img](https://miro.medium.com/max/700/1*P9q0tkeaRY2l1JOXaVKAig.png)


**Mustache** is a logic-less template syntax. It can be used for HTML, config files, source code — anything. It works by expanding tags in a template using values provided in a hash or object.


`mustache.js` is an implementation of the **mustache** template system in JavaScript. It is often considered the base for JavaScript templating. And, since mustache supports various languages, we don’t need a separate templating system on the server side.


```
Mustache.render(“Hello, {{name}}”, { name: “Sherlynn” });
// returns: Hello, Sherlynn
```

In the above, we see **two braces** around {{ name }}. This is ***Mustache syntax*** to show that it is a **placeholder**. When Mustache compiles this, it will look for the ‘name’ property in the object we pass in, and replace {{ name }} with the actual value, e,g, “Sherlynn”.


![img](https://miro.medium.com/max/700/1*LbqYj87xlazySm6wE0Q2lA.png)



## Article 2: A Guide to Flexbox


### display


This defines a flex container; inline or block depending on the given value. It enables a flex context for all its direct children.


```
.container {
  display: flex; /* or inline-flex */
}
```


### flex-direction


![img](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)


This establishes the main-axis, thus defining the direction flex items are placed in the flex container.


```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```



### flex-wrap


By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property.


```
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```



### flex-flow


This is a shorthand for the flex-direction and flex-wrap properties, which together define the flex container’s main and cross axes. The default value is row nowrap.


```
.container {
  flex-flow: column wrap;
}
```



### justify-content


![img](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)


This defines the alignment along the main axis. It helps distribute extra free space leftover when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size. It also exerts some control over the alignment of items when they overflow the line.


```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
```



### flex-grow


![img](https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg)


This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.


```
.item {
  flex-grow: 4; /* default 0 */
}
```



### flex-shrink


This defines the ability for a flex item to shrink if necessary.


```
.item {
  flex-shrink: 3; /* default 1 */
}
```



### flex-basis


This defines the default size of an element before the remaining space is distributed. It can be a length (e.g. 20%, 5rem, etc.) or a keyword. The auto keyword means “look at my width or height property” (which was temporarily done by the main-size keyword until deprecated). The content keyword means “size it based on the item’s content” – this keyword isn’t well supported yet, so it’s hard to test and harder to know what its brethren max-content, min-content, and fit-content do.


```
.item {
  flex-basis:  | auto; /* default auto */
}
```


### flex


This is the shorthand for flex-grow, flex-shrink and flex-basis combined. The second and third parameters (flex-shrink and flex-basis) are optional. The default is 0 1 auto, but if you set it with a single number value, it’s like 1 0.


```
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```



## Tutorial: Flexbox Froggy

`justify-content` property aligns items horizontally and accepts the following **values**:

- **flex-start**: Items align to the left side of the container.
- **flex-end**: Items align to the right side of the container.
- **center**: Items align at the center of the container.
- **space-between**: Items display with equal spacing between them.
- **space-around**: Items display with equal spacing around them.









