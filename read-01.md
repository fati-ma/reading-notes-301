# RESPONSIVE WEB DESIGN and FLOATS
## Read: 01 - SMACSS and Responsive Web Design 

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### For this class, I will be reading these articles: `Shay Howe’s intro to RWD` and `All About Floats` .

### :pushpin: [Shay Howe’s intro to RWD](https://learn.shayhowe.com/advanced-html-css/responsive-web-design/)
### :pushpin: [All About Floats](https://css-tricks.com/all-about-floats/)


## Article 1: Shay Howe’s intro to RWD

### Responsive Overview
Responsive web design is the practice of building a website suitable to work on every device and every screen size, no matter how large or small, mobile or desktop.

![res](https://hackernoon.com/images/1tjg32bo.jpg)


:one:  **Responsive vs. Adaptive vs. Mobile**

:o:  **Responsive** generally means to react quickly and positively to any change, while **adaptive** means to be easily modified for a new purpose or situation, such as change.
**Mobile**, on the other hand, generally means to build a separate website commonly on a new domain solely for mobile users.


:two:  **Flexible Layouts**

:o:  **Flexible layouts**, is the practice of building the layout of a website with a flexible grid, capable of dynamically resizing to any width. Flexible grids are built using relative length units, most commonly percentages or `em` units. These relative lengths are then used to declare common grid property values such as `width`, `margin`, or `padding`.
Flexible layouts *do not* advocate the use of fixed measurement units, such as pixels or inches.


:o:  **Flexible Grid**
Using the flexible grid formula we can take all of the fixed units of length and turn them into relative units.


### Media Queries

Media queries provide the ability to specify different styles for individual browser and device circumstances, the width of the viewport or device orientation for example.

:one:  **Initializing Media Queries**

There are a couple different ways to use media queries, **using the `@media` rule inside of an existing style sheet**, importing a new style sheet using the @import rule, **or by linking to a separate style sheet from within the HTML document.**
It is ***recommend*** to use the @media rule ***inside of an existing style sheet*** to avoid any additional HTTP requests.

HTML
```
<link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
```

CSS
```
/* @media Rule */
@media all and (max-width: 1024px) {...}

/* @import Rule */
@import url(styles.css) all and (max-width: 1024px) {...}
```


:two:  **Logical Operators in Media Queries**

**Logical operators** in media queries help build powerful expressions. There are three different logical operators available for use within media queries, including `and`, `not`, and `only`.


:three:  **Media Features in Media Queries**

:o: **Height & Width Media Features**

The `height` and `width` features are based off the height and width of the viewport rendering area, the browser window for example. Values for these height and width media features may be any length unit, relative or absolute.
Within responsive design the most commonly used features include `min-width` and `max-width`.

```
@media all and (min-width: 320px) and (max-width: 780px) {...}
```

:o:  **Orientation Media Feature**

The `orientation` media feature determines if a device is in the `landscape` or `portrait` orientation. The **landscape** mode is triggered when the display is wider than taller, and the **portrait** mode is triggered when the display is taller than wider. This media feature plays a large part with mobile devices.


### Flexible Media

The final, equally important aspect to responsive web design involves `flexible` media. As viewports begin to change size media doesn’t always follow suit. Images, videos, and other media types need to be scalable, changing their size as the size of the viewport changes.

One quick way to make media scalable is by using the `max-width` property with a value of `100%`. Doing so ensures that as the viewport gets smaller any media will scale down according to its containers width.


## Article 2: All About Floats

### What is “Float”?

**Float** is a CSS positioning property. 

![float](https://miro.medium.com/max/540/1*gL79pBRvVlMjX0Ovevz96w.png)

Setting the float on an element with CSS happens like this:
```
#sidebar {
  float: right;			
}
```
There are four valid values for the float property. **Left** and **Right** float elements those directions respectively. **None** (the default) ensures the element will not float and **Inherit** which will assume the float value from that elements parent element.


### What are floats used for?

Aside from the simple example of wrapping text around images, floats can be used to create **entire web layouts**.

![float](https://i1.wp.com/css-tricks.com/wp-content/csstricks-uploads/web-layout.png?resize=540%2C240&ssl=1)


### Clearing the Float

An element that has the `clear` property set on it will not move up adjacent to the float like the float desires, but will move itself down past the float. 

BEFORE
![img](https://i1.wp.com/css-tricks.com/wp-content/csstricks-uploads/unclearedfooter.png?resize=540%2C195)

```
#footer {
  clear: both;			
}
```

AFTER
![img](https://i2.wp.com/css-tricks.com/wp-content/csstricks-uploads/clearedfooter.png?resize=540%2C230)


### Problems with Floats

:one: **Pushdown** is a symptom of an element inside a floated item being wider than the float itself (typically an image).

:two:  **Double Margin Bug** if you apply a margin in the same direction as the float, it will double the margin. 

:three:  The **3px Jog** is when text that is up next to a floated element is mysteriously kicked away by 3px like a weird forcefield around the float.

:four:  the **Bottom Margin Bug** is when if a floated parent has floated children inside it, bottom margin on those children is ignored by the parent.




