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

- **`data-*="12"`** custom attributes.

  - Custom properties are an excellent way of communicating application-specific information via JavaScript.

<br>

- **`readonly`** will make a field input unavailable for editing.

<br>
<hr>
<br>
