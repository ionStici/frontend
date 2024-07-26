# Pseudo Classes

Pseudo-classes lets you apply styles based on **element state changes** (e.g. mouse hover).

## Table of Contents

- [Interactive states](#interactive-states)
- [Historic states](#historic-states)
- [Form states](#form-states)
- [Selecting elements by their index, order and occurrence](#selecting-elements-by-their-index-order-and-occurrence)
- [Finding empty elements](#finding-empty-elements)
- [Finding and excluding multiple elements](#finding-and-excluding-multiple-elements)

## Interactive states

States based on user interaction.

### :hover and :active

```
a:hover, a:active { }
```

- `hover` will target an element when the cursor hovers over it.
- `active` will target an element when the user clicks on it.

### :focus :focus-within :focus-visible

```
input:focus { }
label:focus-within { }
button:focus-visible { }
```

- `:focus` selects an element that has received focus
- `:focus-within` will select the element if its parent received focus
- `:focus-visible` selects an element when it received focus via the keyboard

### :target

```
#box:target { }
```

`:target` will select an element that has an `id` matching the URL

## Historic states

### :link and :visited

```
a, a:link, a:visited { }
```

- `:link` will target not visited anchor tags.
- `:visited` will target "visited" anchor tags.

**LVHA rule:** style links with pseudo-classes in this particular order: `:link`, `:visited`, `:hover`, `:active`

## Form states

### :disabled and :enabled

```
button:disabled { }
button:enabled { }
```

- `:disabled` for a form element disabled by the browser.
- `:enabled` the opposite state, though form elements are `:enabled` by default.

### :checked and :indeterminate

```
input[type=radio]:checked { }
```

- `:checked` will target radio buttons or checkboxes that has been checked.
- `:indeterminate` state is when a checkbox is neither checked or unchecked.

### :placeholder-shown

```
input:placeholder-shown { }
```

`:placeholder-shown` will select any input or textarea element that is currently displaying placeholder text.

As soon as there is content in the field, this state will no longer apply.

### Validation states

```
input:valid { }
input:invalid { }
input:in-range { }

input:required { }
input:optional { }
```

- `:valid` and `:invalid` for contexts such as an email field that has a pattern that needs to be matched
- `:in-range` pseudo-class is available if an input has a `min` and `max`

<div></div>

- `:required` will be available for required fields
- `:optional` for fields that are not required

## Selecting elements by their index, order and occurrence

### :first-child and :last-child

```
div:first-child { }
div:last-child { }
```

Select the first or last element in a group of sibling elements.

### :only-child

```
div:only-child { }
```

`:only-child` will select an element that is the only child, no siblings.

### :first-of-type and :last-of-type

```
div:first-of-type { }
div:last-of-type { }
```

These will select the first or last element in a group of sibling elements, that matches the element type.

### :nth-child and :nth-of-type

```
.box div:nth-child(2) { }
.box div:nth-of-type(1) { }
```

Select elements in a group of siblings based on a certain index.

- `:nth-child(even)` will select all even elements.
- `:nth-child(3n+3)` this selects every third item, starting at item 3. The `n` in this expression is the index, which starts at zero the 3 (`3n`) is how much you multiply that index by.

### :only-of-type

```
div:only-of-type { }
```

Select the only element of a certain type in a group of siblings.

## Finding empty elements

### :empty

```
article :empty { }
```

If an element has no children (whitespace as well), the `:empty` pseudo-class applies to them.

Useful when you want to hide empty elements.

## Finding and excluding multiple elements

### :not()

```
div:not(:last-child) { }
```

The negation pseudo-class, selects all elements except the one specified in the parenthesis.

### :is()

[The `:is()` pseudo-class](https://developer.mozilla.org/en-US/docs/Web/CSS/:is)
