# CSS Grid

## Table of Content

- [CSS Grid Guide by CSS-Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [CSS Grid Introduction and Terminology](#css-grid-introduction-and-terminology)
- [CSS Grid Properties](#css-grid-properties)

<br><br>

## CSS Grid Introduction and Terminology

**CSS Grid Layout** is a two-dimensional grid system.

_When working with CSS Grids, use Mozilla Firefox, as it has the best developer tools to visualize the CSS Grid layouts._

- First, create a **Grid Container** with `{ display: grid; }`. Then, all the direct children of the grid container are called **Grid Items**.

- **Row Axis** in the _X direction_ and **Column Axis** in the _Y direction_. Axes are unchangeable in CSS Grids.

- **Grid Line:** the vertical and horizontal lines that divide up the grid items, and separate the columns and the rows. Grid lines are automatically numbered from 1, all the way to the number of rows or columns plus 1.

- **Grid Cell:** the area between 2 adjacent vertical and 2 adjacent horizontal grid lines.

- **Grid Track:** the space between two adjacent grid lines. Think of them as the columns or rows of the grid.

- **Grid Area:** the area surrounded by four or more grid lines.

- **Gutter:** the space between the rows and columns.

<br><br>

## CSS Grid Properties

To set ap a grid, declare the next property to the parent element:

```CSS
.container {
    display: grid;
}
```

By default, grids contain only one column and then each item would be put on a new row.

To manually set the grid columns and rows, and also their sizes, use:

```CSS
.container {
    grid-template-columns: 100px 50%;
    grid-template-rows: 200px 75%;

    /* grid-template: 200px 75% / 100px 50%; */
}
```

These properties defines the number of columns and rows in the grid. So each unit creates a grid track and sets the width or height of each grid track.

`grid-template` is a shorthand property. First the values of each row, then after the slash the size of each column.

Percentages are relative to the entire grid's height in rows, and to the grid's width in columns.

<br>

### **Fraction Unit `fr`**

The `fr` relative unit (specifically for CSS Grids) defines the size of columns or rows as a fraction of the grid's width or height, by expanding to all the space that it can occupy.

```CSS
.container {
    width: 1150px;
    display: grid;
    grid-template-columns: 3fr 7fr 150px;   /* 300px 700px 150px */
}
```

If `fr` is used with other units, then each `fr` represents a fraction of the remaining available space. Useful when we need to occupy the remaining space of the grid and not overflowing its borders.

### **Repeat Function**