[&larr; Back](./README.md)

# Pseudo Elements

Pseudo Elements must be applied to block level elements in order to take effect.

Pseudo-elements style specific parts of an element, it's like adding an extra element without having to add more HTML.

## Table of Content

- [::before and ::after](#before-and-after)
- [::first-letter and ::first-line](#first-letter-and-first-line)
- [::backdrop](#backdrop)
- [::marker](#marker)
- [::selection](#selection)
- [::placeholder](#selection)
- [::cue](#cue)

<br>

## ::before and ::after

```
div::before, div::after { content: ''; }
```

- `::before` and `::after` pseudo-elements create a child element inside an element.
- These child elements will appear on the page only if you define the `content` property.
- The `content` can be any string, even an empty one. You can also add an image `url()`.
- An element can have only one `::before` and one `::after`.
- Single tag elements can't have `::before` and `::after`, exception: `input[type="checkbox"]`
- Target `::before` and `::after` when hovering the original element: `a:hover::after {}`

<br>

## ::first-letter and ::first-line

```
p::first-line { }
span::first-letter { }
```

Select the first line or the first letter of an element containing text.

<br>

## ::backdrop

```
video::backdrop { }
```

For full screen mode elements such as `<dialog>`, you can style the backdrop (the space between the element and the rest of the page).

The `::backdrop` pseudo-element is supported in all major browsers apart from Safari.

<br>

## ::marker

The `::marker` pseudo-element lets you style the bullet or number for a list item or the arrow of a `<summary>` element.

```
il ::market { }
```

Supported CSS properties: `color content white-space font animation transition`

You can change the marker symbol using the `content` property.

<br>

## ::selection

```css
::selection {
  background-color: #333;
  color: #fff;
}
```

The `::selection` pseudo-element allows you to style how selected text looks.

Supported CSS properties: `color background-color` and text properties

<br>

## ::placeholder

```
input::placeholder { }
```

Style the placeholder text of input elements.

<br>

## ::cue

`::cue` allows you to style WebVTT cues, which are the captions of a `<video>` element.

You can also pass a selector into a `::cue`, which allows you to style specific elements inside a caption.

```
video::cue { color: yellow; }
video::cue(b) { color: red; }
video::cue(i) { color: lightpink; }
```

<br>
