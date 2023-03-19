[&larr; Back](./README.md)

# Attributes

**Attributes** provide extra information about and functionality for the element.

```html
<p class="text" id="unique" open>Hello</p>
```

<br>

- **Attributes anatomy**

  1. The attribute name, followed by an equal sign.
  2. The attribute value, wrapped in single or double quote marks.

<br>

- **Global attributes** can be set on any HTML element.
- Examples: `id` , `class` , `style` - [mdn list](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)

<br>

- If a **Boolean attribute** is present, it is always true, otherwise it's not.
- Boolean values can either be omitted, empty string, or equal to the name of the attribute.

<br>

- **Enumerated attributes** have a default value if the attribute is present but the value is missing.
- The default value depends on the attribute. Attributes aren't automatically "true" if present.

<br>

- Attribute values that are part of the HTML specification are _case-insensitive_.
- Attribute values that we define, such as classes, are _case-sensitive_.

<br>
<hr>
<br>

- **`tabindex`** enable an element to receive focus.

  - `-1` will make the element capable of receiving focus via JS, but not through tab.
  - `0` will make the element focusable and reachable via tabbing (default tab order, recommended).
  - A value of `1` or more puts the element into a prioritized focus sequence (not recommended).
  - If a document includes elements with a `tabindex` of `1` and more, tabbing begins in a separate sequence, in order of lowest value to highest value, before going through those in the regular sequence in source order.

<br>

- **`contenteditable`** enumerated attribute will make an element editable, focusable, with `tabindex` set to `0`.

<br>

- **`data-*="12"`** custom attributes.

  - Custom properties are an excellent way of communicating application-specific information via JavaScript.

<br>

- **`readonly`** will make a field input unavailable for editing.

<br>

- **`download`** specifies that the target file from `href` will be downloaded when the user clicks on the hyperlink.

  ```HTML
  <a href="/file.jpg" download>Download File</a>
  ```

<br>
<hr>
<br>
