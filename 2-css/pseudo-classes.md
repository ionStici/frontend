[&larr; Back](./selectors.md)

# Pseudo Classes

Pseudo-classes lets you apply styles based on element state changes (e.g. mouse hover).

## Table of Content

- [Interactive states](#interactive-states)
- [Historic states](#historic-states)
- [Form states](#form-states)

<br>

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

<br>

## Historic states

### :link and :visited

```
a, a:link, a:visited { }
```

- `:link` will target not visited anchor tags.
- `:visited` will target "visited" anchor tags.

**LVHA rule:** style links with pseudo-classes in this particular order: `:link`, `:visited`, `:hover`, `:active`

<br>

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

<br>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

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
