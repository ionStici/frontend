## Introduction to Forms

```html
<form action="https://www.url-where-data-send.com/" method="POST">
  <!--  -->
  <label for="first-name">First Name</label>
  <input id="first-name" name="first-name" type="text" />
  <!--  -->
  <input type="submit" value="Submit Form" />
  <button type="submit">Submit Form</button>
  <!--  -->
</form>
```

<br>

- `action` and `method` attributes, require the URL where the data should be sent, and the HTTP protocol method.
- For submitting the form, we can use the `input` or `button` elements.

<br>

- The data sent is made up of _name / value_ pairs.
- The **name** is the value of the `name` attribute.
- The **value** is the user input data.
- For `input` elements where the user can't edit the value, we should define a `value` attribute.

<br>

- [MDN Input Types](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input)
- On a device with a dynamic keyboard, the input type used determines the type of keyboard displayed.
- For example, type `tel` will show a keypad optimized for entering numbers.
- `<form novalidate>` or `<button formnovalidate>` prevents validation.

<br>

## Radio / checkboxes / label / fieldset

```html
<fieldset>
  <legend>Select</legend>
  <!--  -->
  <label><input type="radio" name="same" value="1" checked />Radio 1</label>
  <label><input type="radio" name="same" value="2" required />Radio 2</label>
  <!--  -->
  <label><input type="checkbox" name="check" value="1" required />1</label>
  <label><input type="checkbox" name="check" value="2" required />2</label>
</fieldset>
```

- Groups of form controls are wrapped inside `<fieldset>`, and then labeled by `<legend>`.
- `<fieldset>` supports the `name`, `disabled`, `form` attributes. When we disable a fieldset, all nested form controls are disabled. The fieldset itself is not included in submitted data.
- `legend` provides a label for a group of form controls, and `label` provides a label for individual inputs.
- Include explicit error messages when fields are not correctly filled.

<br>

- `<input type="radio" />` radio button
- The only-one-can-be-selected effect is created by giving each radio button in a group the same `name`.
- The `name` and `value` of the selected radio button are submitted with the form.
- The `checked` attribute will check the radio button.
- Use the `required` attribute to at least one of the controls to force the user to pick a radio button.

<br>

- `<input type="checkbox" />` checkbox input.
- Only selected checkboxes have their `name` and `value` submitted with the form.
- A checkbox with the `required` attribute does not impact other checkboxes with the same name.

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

## Accessing the microphone and camera

```html
<input type="file" capture="user" accept="image/*" />
```

- The `file` input type enables uploading files via forms.
- [`accept`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/accept) describes which file types to aloow. It takes as its value a comma-separated list of one or more file types.
- `capture` enumerated attribute: a new media file created using the user's camera or microphone.

<br>

## Additional attributes

- **`readonly`** will make a field input unavailable for editing.

`required`

`optional`

`default`

`enabled`

`disabled`

`read-write`

`valid`

`invalid`

`in-range`

`out-of-range`

`user-invalid`

`user-valid`

<br>
