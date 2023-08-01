[&larr; Back](./selectors.md)

# Pseudo Classes

## Table of Content

- [Pseudo-Classes](#pseudo-classes)
- [link and visited](#link-and-visited)
- [hover and active](#hover-and-active)
- [before and after](#before-and-after)
- [not()](#not)
- [focus](#focus)
- [checked](#checked)

<br>

## Pseudo-Classes

Pseudo-Class is a special state of a selector. Single color `:`

<br>

### link and visited

```
a, a:link, a:visited { }
```

- `link` will target not clicked anchor tags.
- `visited` will target anchor tags which ahve been clicked.

<br>

### hover and active

```
a:hover, a:active { }
```

- `hover` will target an element when the user hovers it.
- `active` will target an element when the user clicks on it.

<br>

### before and after

```
div::before, div::after { }
```

- `before` and `after` pseudo classes will generate like a virtual element around its parent which we can style.

<!-- <details open> -->
<details>
<summary>More about before and after</summary>
<br>
Pseudo-classes are treated like child of the original element.

<br>

For before or after to appear on the page, we need to define the content property, we can set it to empty string `""`, otherwise it will not appear.

```
a::before { content: ""; }
```

<br>

Target after or before when hover the original element:

```
a:hover::after { }
```

</details>

<br>

### not()

```
div:not(:last-child) { }
```

The negation pseudo class, selects all elements expect the specified one in parenthesis.

<br>

### focus

```
input:focus { }
```

Selects an element that has received focus.

<br>

### checked

```
input[type=radio]:checked { }
```

Will target radio buttons or checkboxes that has been checked.

<br>
