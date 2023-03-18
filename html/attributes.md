[&larr; Back](./README.md)

# Attributes

HTML Elements can have attributes.

```html
<p class="text" open="open" open>Paragraph</p>
```

Attributes anatomy:

1. The attribute name, followed by an equal sign.
2. The attribute value, wrapped in single or double quote marks.

Attributes contain extra information about the element. It will not appear on the page.

_Boolean attributes_ can only have one value which is generally the same as the attribute name.

We can set boolean attribute equal to itself, or leave just the name - both acceptable.

<br>

## `download`

```HTML
<a href="/file.jpg" download>Download File</a>
```

Specifies that the target file (specified in href) will be downloaded when user clicks on the hyperlink.

<br>

## `contenteditable`

```HTML
<p contenteditable="true">Editable</p>
```

Specifies whether the content of an element is editable or not.

<br>

## `autocomplete`

```HTML
<input type="text" autocomplete="off" />
```

`autocomplete` allows the browser to predict the value.

<br>

## `spellcheck`

```HTML
<input type="text" spellcheck="true" />
```

Checks the spelling.

<br>

## `readonly`

```HTML
<input type="text" readonly />
```

The field is read-only and can not be edited.
