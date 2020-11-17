# Readings: CSS GRID
## Read:04 - Responsive Web Design and Regular Expressions

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-04).

### For this class, I will be reading from this resource: `GRID GARDEN`.

### :pushpin: [GRID GARDEN](https://cssgridgarden.com/)


## Tutorial: GRID GARDEN


1. `grid-column-start` 

The grid item by default will span exactly one column. However, to extend the item across multiple columns by adding the `grid-column-end` property.

If we want to count grid lines from the right instead of the left, we can give `grid-column-start` and `grid-column-end` **negative values**. For example, we can set it to *-1* to *specify the first grid line from the right*.

Instead of defining a grid item based on the start and end positions of the grid lines, you can define it based on your *desired column width* using the `span` keyword. Keep in mind that span only works with **positive values**.

We can also use the `span` keyword with `grid-column-start` to ***set our item's width relative to the end position***.

`grid-column` is a ***shorthand property*** that can accept both values at once, separated by a slash.

For example, `grid-column: 2 / 4;` will set the grid item to start on the 2nd vertical grid line and end on the 4th grid line.
The `span` keyword also works with this shorthand property.


2. `grid-row-start`

One of the things that sets CSS grids apart from flexbox is that you can easily position items in two dimensions: columns and rows. `grid-row-start` works much like `grid-column-start` **except** along the vertical axis.


3. `grid-area`

`grid-area` accepts *four values* separated by **slashes**: `grid-row-start`, `grid-column-start`, `grid-row-end`, followed by `grid-column-end`.
One *example* of this would be `grid-area: 1 / 1 / 3 / 6;`.


4. `order`

If grid items aren't *explicitly* placed with `grid-area`, `grid-column`, `grid-row`, etc., they are *automatically* placed according to their `order` in the source code. We can override this using the `order` property, which is one of the advantages of grid over table-based layout.
**By default**, *all grid items have an order of 0*, but this can be set to any positive or negative value, similar to z-index.


5. `grid-template-columns`

`grid-template-columns: 20% 20% 20% 20% 20%;` and `grid-template-rows: 20% 20% 20% 20% 20%;` Each rule has *five values* which create *five columns*, each set to *20% of the overall width*.

Specifying a bunch of columns with identical widths can get tedious. Luckily there's a `repeat` function to help with that.
For example, we previously defined **five 20% columns** with the rule `grid-template-columns: 20% 20% 20% 20% 20%;`. This can be simplified as `grid-template-columns: repeat(5, 20%);`.

`grid-template-columns` doesn't just accept values in *percentages*, but also length units like **pixels and ems**. You can even mix different units together.

Grid also introduces a new unit, the fractional `fr`. Each `fr` unit allocates one share of the available space. For example, if two elements are set to *1fr* and *3fr* respectively, the space is divided into *4 equal shares*; the first element occupies 1/4 and the second element 3/4 of any leftover space.
`grid-template-columns: 1fr 5fr;`

When columns are set with pixels, percentages, or ems, any other columns set with fr will divvy up the space that's left over.

`grid-template-columns : 75px 3fr 2fr;`


6. `grid-template`

`grid-template` is a shorthand property that **combines** `grid-template-rows` and `grid-template-columns`.
*For example*, `grid-template: 50% 50% / 200px;` will create a grid with two rows that are 50% each, and one column that is 200 pixels wide.



