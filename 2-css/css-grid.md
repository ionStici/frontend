[&larr; back](./README.md)

# **CSS Grid**

## Table of Content

- [CSS Grid Introduction and Terminology](#css-grid-introduction-and-terminology)
- [CSS Grid Properties Overview](#css-grid-properties-overview)
- [Grid Container](#grid-container)
- [Grid Items](#grid-items)
- [Grid Template Areas](#grid-template-areas)

<br>

- [Grid Concepts](#grid-concepts)
- [Fraction Unit](#fraction-unit)
- [min-content / max-content / fit-content](#min-content--max-content--fit-content)
- [repeat() function](#repeat-function)
- [minmax() function](#minmax-function)
- [auto-fit / auto-fill](#auto-fit--auto-fill)

<br>

- [Alignment](#alignment)
- [Justify Items and Align Items](#justify-items-and-align-items)
- [Justify Self and Align Self](#justify-self-and-align-self)
- [Justify Content and Align Content](#justify-content-and-align-content)

<br>

- [Explicit vs. Implicit](#explicit-grids-vs-implicit-grids)
- [Grid Auto Properties](#grid-auto-properties)
- [Grid Auto Flow](#grid-auto-flow)

<div></div>

### External Resources

- [web.dev | CSS Grid](https://web.dev/learn/css/grid)
- [A Complete Guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

<br>

## CSS Grid Introduction and Terminology

- **CSS Grid Layout** is a two-dimensional grid system.
- Create a **Grid Container** with `{ display: grid; }` and then all the direct children are called **Grid Items**.
- **Row Axis** in the _X direction_ and **Column Axis** in the _Y direction_. Axes are unchangeable in CSS Grids.
- **Grid Line:** the vertical and horizontal lines that divide up the grid items, and separate the columns and the rows.
- **Grid Cell:** the area between 2 adjacent vertical and 2 adjacent horizontal grid lines.
- **Grid Track:** the space between two adjacent grid lines. Think of them as the columns or rows of the grid.
- **Grid Area:** the area surrounded by four or more grid lines.
- **Gutter:** the space between the rows and columns.

## CSS Grid Properties Overview

| Container Properties  | Aligning (Container) |  Grid Gap  |  Implicit Grids   |
| :-------------------: | :------------------: | :--------: | :---------------: |
|  grid-template-rows   |    justify-items     |    gap     |  grid-auto-rows   |
| grid-template-columns |     align-items      |  row-gap   | grid-auto-columns |
|  grid-template-areas  |   justify-content    | column-gap |  grid-auto-flows  |
|     grid-template     |    align-content     |     -      |         -         |

|  Item Properties  | Aligning (Items) |
| :---------------: | :--------------: |
|  grid-row-start   |   justify-self   |
|   grid-row-end    |    align-self    |
| grid-column-start |      order       |
|  grid-column-end  |        -         |
|     grid-row      |        -         |
|    grid-column    |        -         |
|     grid-area     |        -         |

## Grid Container

_Use Mozilla Firefox when working with CSS Grids, as it has the best developer tools to visualize the CSS Grid layouts._

To set ap a grid, declare the next property to the parent element:

```CSS
.grid {
    display: grid;
}
```

By default, grids contain only one column and then each item would be put on a new row.

To manually set the grid columns and rows, and also their sizes, use:

```CSS
.grid {
    grid-template-columns: 100px 50%;
    grid-template-rows: 200px 75%;

    /* grid-template: 200px 75% / 100px 50%; */
}
```

These properties define the number of columns and rows in the grid. So each unit creates a grid track and sets the width or height of each grid track.

`grid-template` is a shorthand property. First the values of each row, then after the slash the size of each column.

Percentages are relative to the entire grid's height in rows, and to the grid's width in columns.

`grid-template-rows: auto` can be thought of as being as big as the content. Tracks are auto sized by default.

### Grid Gap

`row-gap` and `column-gap` will insert blank space between every row and column in the grid (but not on the outer edges).

```CSS
.grid {
    row-gap: 50px;
    column-gap: 100px;

    /* gap: 100px 50px; */
}
```

`gap` is a shorthand property, first rows gap and then columns gap, or we can specify just one value.

This properties: `grid-row-gap grid-column-gap grid-gap` are deprecated.

## Grid Items

We can expand grid items on multiple rows or columns by using the properties below:

```CSS
.item {
    grid-row-start: 3;
    grid-row-end: span 2;
    /* grid-row: 3 / span 2; */

    grid-column-start: 1;
    grid-column-end: -1;
    /* grid-column: 1 / -1; */

    /* grid-area: 3 / 1 / span 2 / -1; */
}
```

We manually define how many rows or columns the grid item should take by specifying the grid lines.

We can explicitly tell how many rows or columns to span by using the `span` keyword.

_When spanning explicitly, we can have multiple grid items in the same cell overlapping each other. To set different elements on top of each other, use the `z-index` property to create stacking contexts._

In case the grid item spans multiple rows or columns, it will also include the gap if any exists.

`-1` means all the way until the end of the explicit grid.

Grid lines are automatically numbered from 1 to the number of rows or columns plus 1.

`grid-row` and `grid-column` are shorthand properties. The starting row or column goes before the slash and the ending row or column goes after it.

`grid-area` this shorthand property set the starting and ending positions for both the rows and columns of an item in the following order: `row start / column start / row end / column end`.

The code example above translates to: the grid item starts on row 3 and spans 2 rows, then starts on column 1 until the last column line.

## Grid Template Areas

The `grid-template-areas` and `grid-area` properties distribute the grid items to specific named grid cells.

```HTML
<div class="grid">
    <header class="header"></header>
    <section class="box-1"></section>
    <section class="box-2"></section>
</div>
```

```CSS
.grid {
    display: grid;
    max-width: 1000px;
    margin: 50px auto;

    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 1fr 1fr;

    grid-template-areas: 'head head head'
                         'box1 box2  .  ';
}

header { grid-area: head; }
.box-1 { grid-area: box1; }
.box-2 { grid-area: box2; }
```

We can leave a cell empty by putting a dot `'.'` instead of a name.

After creating the rows and columns, we can name each grid cell with `grid-template-areas` and then place each grid item with `grid-area` by providing the cell name.

### Named Grid Lines

Giving names to grid lines.

```css
.grid {
  display: grid;
  grid-template-columns:
    [main-start aside-start] 1fr
    [aside-end content-start] 2fr
    [content-end main-end];
}

.sidebar {
  grid-column: aside-start / aside-end;
}

footer {
  grid-column: main-start / main-end;
}
```

We name the lines on the grid between square brackets, and then we use them on grid items instead of the numbers.

<br>

## Grid Concepts

### Fraction Unit

The `fr` relative unit (specifically for CSS Grids) defines the size of columns or rows as a fraction of the grid's width or height, by expanding to all the space that it can occupy.

```CSS
.grid {
    width: 1150px;
    display: grid;
    grid-template-columns: 3fr 7fr 150px;   /* 300px 700px 150px */
}
```

If `fr` is used with other units, then each `fr` represents a fraction of the remaining available space. Useful when we need to occupy the remaining space of the grid and not overflowing its borders.

### min-content / max-content / fit-content

```CSS
.grid {
    grid-template-rows: max-content min-content fit-content(10em) 100px;
}
```

- `min-content` sizing keyword will make a track as small as it can be without the track content overflowing. For text content this means that the content will take all soft-wrapping opportunities, becoming as small as the longest word.

- `max-content` sizing keyword will make a track as wide enough for all of the content to display in one long unbroken string.For text content this means that the content will not wrap at all even if it causes overflows.

- The `fit-content` function acts like max-content, but once the track reaches the size that you pass into the function, the content starts to wrap.

### repeat function

The repeat function (created specifically for CSS Grids) duplicates the specified units inside the grid template properties a given number of times.

```CSS
.grid {
    grid-template-columns: repeat(3, 1fr);
    /* grid-template-columns: 1fr 1fr 1fr; */
}
```

This will split the grid into three equal columns. Also, we can repeat sections: `repeat(3, 1fr 2fr)`

_p.s._ We can specify multiple units in the repeat() function and then each group of units will be duplicated the given number of times.

### minmax function

Preventing a track from getting too big or too small.

```CSS
.grid {
    grid-template-columns: 100px minmax(100px, 1fr) 100px;
}
```

The `minmax()` function requires 2 values and enables the track to vary between these 2 values as the overall grid resizes. In the code example above, the second column width will always be between 100px and 1fr wide.

### auto-fit / auto-fill

```CSS
.grid {
    width: 1000px;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
```

- `auto-fill` creates automatically as many tracks with the indicated width as it fits in the container. Above it created 10 tracks with 100px each item (1000 / 100).

```CSS
.grid {
    width: 1000px;
    display: grid;
    grid-template-columns: repeat(auto-fit, 100px);
}
```

- `auto-fit` same as auto-fill, except that empty tracks are collapsed, giving them a width of zero.

<br>

## Alignment

### Justify Items and Align Items

```CSS
.grid {
    justify-items: center;
    align-items: center;
}
```

`justify-items` (declared on grid containers) positions grid items horizontally from left to right inside their grid cell.

`align-items` (declared on grid containers) positions grid items vertically from top to bottom inside their grid cell.

_Most important values for both properties:_

- `stretch` (by default) stretches all items to fill the grid cell. If an item has the width / height declared, then it will not be stretched.
- `start`, `end` and `center` will position the items inside their columns. The items will be as wide / tall as their current width / height.

### Justify Self and Align Self

```CSS
.item {
    justify-self: center;
    align-self: center;
}
```

Similar with `justify-items` and `align-items`, _both pairs accept the same values_, but `justify-self` and `align-self` work on individual **grid items**, so they must be declared on grid items.

Note that these two will override the `justify-items` and `align-items` properties.

`justify-self` and `align-self` positions individual grid items horizontally / vertically.

### Justify Content and Align Content

These (grid container) properties will only work if there is additional space to distribute along the container.

```CSS
.grid {
    justify-content: stretch;  /* by default */
    align-content: stretch;    /* by default */

}
```

- `justify-content` positions the columns inside the grid container horizontally from left to right.
- `align-content` positions the rows vertically from top to bottom.

_Most important values for both properties:_

- `stretch` stretches the grid items until reaches the full width / height of the grid container.
- `start`, `end`, `center`
- `space-around`, `space-between`, `space-evenly`

<br>

## Explicit Grids vs. Implicit Grids

**Explicit Grid** - the grid that we define.
**Implicit Grid** - the grid that CSS algorithm automatically builds when there are more elements than fit in the grid that we explicitly specified.

Implicit Grids use case: when we don't know from the beginning how many rows or columns we need.

The default behavior of implicit grids: new rows will be added for new grid items. The new rows will be tall enough to contain the content within them.

### Grid Auto Properties

```CSS
.grid {
    grid-auto-rows: 500px;
    grid-auto-columns: 750px;
}
```

Two properties (declared on grid containers) for specifying the size of grid tracks added implicitly:

- `grid-auto-rows` specifies the height of implicitly added grid rows.
- `grid-auto-columns` specifies the width of implicitly added grid columns.

These two properties accept units as values.

If we do not specify `grid-auto-rows`, then the rows will be auto-adjusted to the height of the content of the grid items.

### Grid Auto Flow

We can specify the order in which rows and columns are implicitly rendered.

```CSS
.grid {
    grid-auto-flow: row dense;
}
```

`grid-auto-flow` specifies whether new elements should be added to rows or columns.

- `row` (default) new elements fill rows from left to right and create new rows when there there are to many grid items.
- `column` new elements fill columns from top to bottom and create new columns when there are too many grid items.
- `dense` keyword fill holes in the grid layout with grid cells if smaller elements are added.

We can pair `row` and `column` with `dense`.

<br>
