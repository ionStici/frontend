[&larr; back](./README.md)

# Form Elements in Depth

## Table of Content

- [The form element](#the-form-element)

<br>

## The form element

The `<form>` is a container for interactive form controls.

When you need to store or process data from users, you should use the `<form>` element.

**Form submission:** when we submit a `<form>`, the browser checks its attributes. The data is processed according to the `method` attribute. If no `method` attribute is present, a `GET` request is made to the URL of the current page.

The submitted data can be handled by JavaScript on the frontend using a `GET` request, or by code on the backend using a `GET` or `POST` request.

When the form is submitted, the browser makes a request to the URL that is the value of the `action` attribute.

If the Submit button has a `formmethod` or `formaction` attribute, it will use them instead.

<br>
