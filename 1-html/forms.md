[&larr; Back](./README.md)

# Forms

## Table of Content

- [Form elements](#form-elements)
- [List of options](#list-of-options)

<br>

## Form elements

The **`<form>`** document landmark is a container with interactive controls for submitting information.

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

- **Submitting a Form** - the browser makes a request to the URL specified in the `action` attribute, with all the data from the form controls.

  - The **`<button>`** element can be used to submit a form.
  - Use `<button type="button">` in case you want to disable the default submit behavior.
  - `<input type="submit" value="Submit">` can substitute the button element.
  - A form can also be submitted by using the `Enter` key when a form field has focus.

<br>

## List of options

Using `<select>` and `<option>`, we can create a dropdrown form control.

```html
<label for="color">Color</label>
<select id="color" name="color">
  <option value="orange" selected>Orange</option>
  <option value="green">Green</option>
</select>
```

These elements will submit a name / value pair from the selected option, e.g. "color" associated with "orange".

The `selected` attribute will pre-select one option.

<br>

## Grouping form controls

<br>
