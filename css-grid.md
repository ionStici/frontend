# CSS Grid

- [Grid Container]()
  - [Grid Gap]()
- [Grid Items]()
- [Grid Concepts]()
  - [Fraction Unit `fr`]()
  - [repeat() function]()
  - [minmax() function]()

<br>

## Grid Container

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

These properties defines the number of columns and rows in the grid. So each unit creates a grid track and sets the width or height of each grid track.

`grid-template` is a shorthand property. First the values of each row, then after the slash the size of each column.

Percentages are relative to the entire grid's height in rows, and to the grid's width in columns.

<br>

### Grid Gap

`row-gap` and `column-gap` will insert space between every row and column in the grid (not on the outer edges).

```CSS
.grid {
    row-gap: 50px;
    column-gap: 100px;

    /* gap: 100px 50px; */
}
```

`gap` is a shorthand property, first rows gap and then columns gap.

If only one value is given, it will set the column gap and the row gap to that value.

Note: You might have seen grid-row-gap, grid-column-gap, and grid-gap in other code, but these properties are now deprecated.

<br>

## Grid Items

We can expands grid items on multiple rows or columns by using the properties below:

```CSS
.item {
    grid-row-start: 3;
    grid-row-end: 4;
    /* grid-row: 3 / 4; */

    grid-column-start: 1;
    grid-column-end: -1;
    /* grid-column: 1 / -1; */

    /* grid-area: 3 / 1 / 4 / -1; */
}
```

We manually define how many rows or column the grid item should take by specifying the grid lines.

`-1` means all the way until the end of the explicit grid.

Grid lines are automatically numbered from 1 to the number of rows or columns plus 1.

`grid-rea` is a shorthand property. ..

The code example above translates to: the grid item starts from row 3 to row 4 and from column 1 to the last column.

<br>

## Grid Concepts

<br>

### Fraction Unit `fr`

The `fr` relative unit (specifically for CSS Grids) defines the size of columns or rows as a fraction of the grid's width or height, by expanding to all the space that it can occupy.

```CSS
.grid {
    width: 1150px;
    display: grid;
    grid-template-columns: 3fr 7fr 150px;   /* 300px 700px 150px */
}
```

If `fr` is used with other units, then each `fr` represents a fraction of the remaining available space. Useful when we need to occupy the remaining space of the grid and not overflowing its borders.

<br>

### repeat() function

The repeat function (created specifically for CSS Grids) duplicates the specified units inside the grid template properties a given number of times.

```CSS
.grid {
    grid-template-columns: repeat(3, 1fr);
    /* grid-template-columns: 1fr 1fr 1fr; */
}
```

This will split the grid into three equal columns.

_p.s._ We can specify multiple units in the repeat() function and then each group of units will be duplicated the given number of times.

<br>

### minmax() function

Preventing a track from getting too big or too small.

```CSS
.grid {
    grid-template-columns: 100px minmax(100px, 200px) 100px;
}
```

The minmax() function requires 2 values and enables the track to vary between these 2 values as the overall grid resizes. In the code example above, the second column width will always be between 100px and 200px wide.
