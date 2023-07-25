[&larr; Back](./README.md)

# Forms

## Table of Content

- [Form elements](#form-elements)

<br>

## Form elements

The `<form>` element is a container for different types of input elements.

```html
<form>
  <label for="name">Your Name:</label>
  <input type="text" id="name" name="name" />
  <button>Submit</button>
</form>
```

- The **`label`** element is used describe input elements. Labels improve accessibility.

  - Explicit label: the `for` attribute should match the `id` of the form control.
  - Implicit label: include the form control inside the `label` element.

<br>

- The **`input`** element is used to gather input from users.

  - The `name` attribute acts as an identifier for the user-entered data, in a name / value manner.
  - The `type` attribute defines the [form control type from a big variety.](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input)

<br>

- The **`<textarea>`** element will render a text box where we can enter multiple lines of text (label requried).

<br>
