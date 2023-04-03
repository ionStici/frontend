[&larr; Back](./selectors.md)

# Pseudo

## Table of Content

- [Pseudo-Classes](#pseudo-classes)
  - [link and visited](#link-and-visited)
  - [hover and active](#hover-and-active)
  - [before and after](#before-and-after)
  - [not()](#not)
  - [focus](#focus)
  - [checked](#checked)
- [Pseudo-Selectors](#pseudo-elements)
  - [first-line and first-letter](#first-line-and-first-letter)
  - [first-child and last-child](#first-child-and-last-child)
  - [selection](#selection)
  - [nth-child](#nth-child)

<br>

## Pseudo-Classes

Pseudo-Class is a special state of a selector.

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

## Pseudo-Elements

Pseudo Elements must be applied to block level elements in order to take effect.

Pseudo Elements style specific parts of an element.

<br>

### first-line and first-letter

```
p::first-line { }
span::first-letter { }
```

Select the first line or the first letter of an element containing text.

<br>

### first-child and last-child

```
div:first-child { }
div:last-child { }
```

Will select the first child of the last child of the parent element.

<br>

### selection

```css
::selection {
  background-color: #333;
  color: #fff;
}
```

Applies styles to the part of a document that has been highlighted by the user (such as selected text).

<br>

### nth-child

```
li:nth-child(3) { }
li:nth-child(4n) { }
```

Accepts an integer as a parameter, not zero based.

1. Select a specific element in a stack.
2. Select every fourth list item.
