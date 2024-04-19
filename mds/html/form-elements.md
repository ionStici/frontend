[&larr; back](./README.md)

# Form Elements in Depth

## Table of Content

- [The form element](#the-form-element)
- [Form Fields](#form-fields)
- [Form Attributes](#form-attributes)

<br>

## The form element

The `<form>` is a container for interactive form controls.

When you need to store or process data from users, you should use the `<form>` element.

**Form submission:** when we submit a `<form>`, the browser checks its attributes. The data is processed according to the `method` attribute. If no `method` attribute is present, a `GET` request is made to the URL of the current page.

The submitted data can be handled by JavaScript on the frontend using a `GET` request, or by code on the backend using a `GET` or `POST` request.

When the form is submitted, the browser makes a request to the URL that is the value of the `action` attribute.

If the Submit button has a `formmethod` or `formaction` attribute, it will use them instead.

<br>

## Form Fields

- `<input type="text" />` for inserting text.
- `<textarea>` for longer text, the element is scrollable and resizable.

<div></div>

- `tel` for telephone numbers
- `email` for email addresses
- `date` for dates

<div></div>

- `password` for passwords
- `hidden` for unique security tokens. The input can't be seen or modified by users.
- `range` for choosing between a range of numbers

<div></div>

- `radio` for radio buttons.
  - The only-one-can-be-selected effect is created by giving each radio button in a group the same `name`.
  - The `name` and `value` of the selected radio button are submitted with the form.
  - The `checked` attribute will check the radio button.
  - Use the `required` attribute to at least one of the controls to force the user to pick a radio button.

<div></div>

- `checkbox` checkbox input
  - Only selected checkboxes have their `name` and `value` submitted with the form.
  - A checkbox with the `required` attribute does not impact other checkboxes with the same name.

<br>

## Form Attributes

- **`readonly`** will make a field input unavailable for editing.
- The Boolean **`disabled`** attribute, makes the element not mutable, focusable, or submitted with the form. Whent he form is submitted, you may want to disable the Submit button.
- Use the **`value`** attribute to show values already completed.

### Other

- **`optional`**

- **`default`**

- **`enabled`**

- **`read-write`**

- **`in-range`**

- [**`inputmode`**](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/inputmode)

<br>
