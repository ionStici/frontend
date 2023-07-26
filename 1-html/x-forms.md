## Radio / checkboxes

<br>

- On a device with a dynamic keyboard, the input type used determines the type of the keyboard displayed. E.g. the type `tel` will show a keypad optimized for entering numbers.

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

<!-- ## Accessing the microphone and camera

```html
<input type="file" capture="user" accept="image/*" />
```

- The `file` input type enables uploading files via forms.
- [`accept`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/accept) describes which file types to allow. It takes as its value a comma-separated list of one or more file types.
- `capture` enumerated attribute: a new media file created using the user's camera or microphone.

<br>

## Additional attributes

- **`readonly`** will make a field input unavailable for editing.



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

<br> -->
