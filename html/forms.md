# HTML Forms

```html
<form action="/example.html" method="POST">
  <label for"first-name">First Name</label>
  <input type="text" name="first-name" value="John" id="first-name" />
</form>
```

<hr>

<details>

<summary>form</summary>

<br>

An HTML `<form>` element is responsible for collecting information to send somewhere else.

<div></div>

- The `action` attribute determines where the information is sent.

<div></div>

- The `method` attribute is assigned a HTTP verb that is included in the HTTP request.

</details>

<hr>

<details>
<summary>input</summary>

<br>

<div></div>

- The `<input>` self-closing element allows you several ways to collect data from a web form.

<div></div>

- The `type` attribute of the `<input>` element determines how it renders on the web page and what kind of data it can accept, for example: `text`, `email`, `password`, etc.

<div></div>

- The `<input>` element must contains a `name` attribute set to a value that represents the data that the input is supposed to receive from the user. For example, for the user's first name, we can write: `name="first-name"`. Without the `name` attribute, the information in the `<input>` won't be sent when the `<form>` is submitted.

<div></div>

- After users type into the `<input>` element, the value of the `value` attribute becomes what is types into the text field. The value of the `value` attribute is paired with the value of the `name` attribute and set as text when the form is submitted. We could also assign a default value for the `value` attribute so that users have a pre-filled text field.

</details>

<hr>

<details>
<summary>label</summary>

<br>

The `<label>` element contains explanatory text for the input fields.

To associate a `<label>` and an `<input>`,

<div></div>

</details>

<hr>

<!-- ```html
<label>
  elements are used to associate descriptive text for an input element
  (especially for assistive technologies like screen readers). Example:
  <label>First Name <input type="text" /></label>
  This make it so clicking the word “First Name” - selects the corresponding
  input element.

  <label>
    Select me <input type="radio" name="age" value="18" id="18" />
  </label>
  If you select a radio button and then submit the form, the form data for the
  radio buttons is based on its name and value attributes. For convenience, set
  the button’s value attribute to the same value as its id attribute. - To make
  it so selecting one radio button automatically deselects the other ones, all
  radio buttons must have a name attribute with the same value.</label
>
``` -->
