# Forms in Practice

## Table of Contents

- [Form elements](#form-elements)
- [List of options](#list-of-options)
- [Grouping Form controls](#grouping-form-controls)
- [The Datalist element](#the-datalist-element)
- [Form validation on the frontend](#form-validation-on-the-frontend)
- [Autofill](#autofill)
- [Upload files](#upload-files)

## Form elements

The **`<form>`** document landmark is a container with interactive controls for submitting information.

The **`action`** and **`method`** attributes, require an URL where the data should be sent, and a HTTP protocol method.

```html
<form action="https://www.url-where-data-send.com/" method="post">
  <label for="name">Your Name:</label>
  <input type="text" id="name" name="name" />
  <button>Submit</button>
</form>
```

- The data sent is made up of **name/value** pairs.

  - The **name** is the value of the `name` attribute. The **value** is the user input data.
  - For `input` elements where the user can't edit the value, we have to define a `value` attribute.

- The **`label`** element is used describe input elements. Labels improve accessibility.

  - Explicit label: the `for` attribute should match the `id` of the form control.
  - Implicit label: include the form control inside the `label` element.

- The **`input`** element is used to gather input from users.

  - The `name` attribute acts as an identifier for the user-entered data, in a name / value manner.
  - The `type` attribute defines the [form control type from a big variety.](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Input)
  - The **`<textarea>`** element will render a text box where we can enter multiple lines of text (use label as well).

- **Submitting a Form** - the browser makes a request to the URL specified in the `action` attribute, with all the data from the form controls.

  - The **`<button>`** element can be used to submit a form. Use `<button type="button">` in case you want to disable the default submit behavior.
  - `<input type="submit" value="Submit">` can substitute the button element.
  - A form can also be submitted by using the `Enter` key when a form field has focus.

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

## Grouping Form controls

Groups of form controls are wrapped inside `<fieldset>` and then labeled by `<legend>`.

```html
<fieldset>
  <legend>Your favorite web technology</legend>

  <label for="html">HTML</label>
  <input type="radio" id="html" name="webfeature" value="html" />

  <label>CSS</label>
  <input type="radio" id="css" name="webfeature" value="css" />
</fieldset>
```

The `legend` element is used to describe the group of form controls, it has to be the very first element in the `fieldset` group. `legend` provides a label for a group of form controls, and `label` provides a label for individual inputs.

`<fieldset>` supports attributes like: `name`, `disabled`, `form`.

- When we disable a fieldset, all nested form controls are disabled. The fieldset itself is not included in submitted data.
- The `form` attribute in `fieldset` requires the `id` value of the `form` container, this indicates to what form the `fieldset` group of elements belongs to.

## The Datalist element

```html
<input type="text" list="colors" />

<datalist id="colors">
  <option value="Orange" />
  <option value="Green" />
</datalist>
```

The `<datalist>` HTML element contains a set of `<option>` elements that represent the permissible or recommended options available to choose from within other controls.

## Form validation on the frontend

- `<form novalidate>` or `<button formnovalidate>` prevents validation.
- The **`required`** attribute makes an input mandatory, and tests if the input matches the format of the `type`.

<div></div>

- Use `minlength` and `maxlength` attributes to set a minimum or maximum number of characters required.
- For numerical input types use `min` and `max` to achieve the same result.

### Communicate your validation rules

```html
<input aria-describedby="password-minlength" type="password" />
<div id="password-minlength">Enter at least eight characters</div>
```

Use `aria-describedby` attribute to connect a form control with an element that explains the rules.

### Pattern attribute

```html
<input pattern="[a-z]{2,20}" />
```

We can define a regular expression as a value for the `pattern` attribute to set constraints.

### Style form controls based on the validation status

- Style `required` fields using the `input:required` CSS pseudo class.
- Use `:invalid` or `:valid` pseudo classes to add styles to invalid and valid form controls.
- The `:user-invalid` behaves like `:invalid`, but styles are only applied after user interaction.

## Autofill

Autofill and autocomplete provide accessibility benefits.

The [**`autocomplete`**](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete) attribute lets web developers specify what if any permission the user agent has to provide automated assistance in filling out form field values, as well as guidance to the browser as to the type of information expected in the field.

`autocomplete="username"` : Suggests to the browser that the field requires a username or account name.

**p.s.** The `:autofill` CSS pseudo-class matches when an `<input>` element has its value autofilled by the browser. The class stops matching if the user edits the field.

For one-time-code fields, turn off the autofill with: `autocomplete="off"`

## Upload files

Use `type="file"` to enable uploading files.

```html
<input type="file" capture="user" accept="image/*" multiple />
```

- The `file` input type enables uploading files via forms.
- Use the `multiple` attribute if users should be able to upload multiple files.
- [`accept`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/accept) describes which file types to allow. It takes as its value a comma-separated list of one or more file types.
- `capture` enumerated attribute: a new media file created using the user's camera or microphone.
- Set `enctype="multipart/form-data"` on the form element to ensure users can upload files. To make sure files can be submitted, change it to `multipart/form-data`. Without this encoding, files can't be sent with a `POST` request.

## More

- [JavaScript Constraint Validation API](https://web.dev/learn/forms/validation/#provide-meaningful-error-messages)
- [Test your forms](https://web.dev/learn/forms/testing/)
