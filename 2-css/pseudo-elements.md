[&larr; Back](./selectors.md)

# Pseudo Elements

## Table of Content

- [Pseudo-Selectors](#pseudo-elements)
- [first-line and first-letter](#first-line-and-first-letter)
- [first-child and last-child](#first-child-and-last-child)
- [selection](#selection)
- [nth-child](#nth-child)

<br>

## Pseudo-Elements

Pseudo Elements must be applied to block level elements in order to take effect.

Pseudo Elements style specific parts of an element. Double color `::`

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

<br>
