[&larr; Back](./README.md)

# Internationalizing Dates

**Internationalization API** - format dates and numbers according to different languages.

## Dates

**`Intl`** is the namespace for the Internationalization API.

For date and time, we use the `Intl.DateTimeFormat()` function.

- **Arg 1:** language and country, for example `"en-US"`.

  The date and time will be formmated according to this language and country.

  [Table with all the languages and countries.](http://www.lingoes.net/en/translator/langcode.htm)

- **Arg 2:** an object with formatting preferences.

Further, we chain the **`format()`** function, with the date we want to format as argument.

```js
new Intl.DateTimeFormat("en-US").format(new Date()); // 9/28/2023
```

Note that the `new` constructor must be used.

### Object with preferences and the locale string

```js
const locale = navigator.language; // en-GB

const options = {
  hour: "numeric",
  minute: "numeric",
  day: "numeric",
  month: "long",
  year: "numeric",
  weekday: "long",
};

const now = new Date();
const date = new Intl.DateTimeFormat(locale, options).format(now);
// Thursday, 28 September 2023 at 10:20
```

<br>
