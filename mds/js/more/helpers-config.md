[&larr; Back](./README.md)

# Helpers and Configuration Files

_Two special modules independent from the rest of the architecture:_

1. Module for the project configurations
2. Module for general helper functions

<br>

## `config.js`

Module for Constants and global settings (e.g. API urls, magic numbers).

`API_URL` we use uppercase for constants, noticing that it should not change.

`TIMEOUT_SECONDS`

<br>

## `helpers.js`

Module for functions that we reuse over and over in out project.

For example: a function named `getJSON` which will get JSON and handle errors.

<br>

## AJAX Helper Function

```js
export const AJAX = async function (url, uploadData = undefined) {
  try {
    const fetchPro = uploadData
      ? fetch(url, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(uploadData),
        })
      : fetch(url);

    const rest = await Promise.race([fetchPro, timeout(TIMEOUT_SECONDS)]);
    const data = await res.json();

    if (!res.ok) throw new Error(`${data.message} (${res.status})`);
    return data;
  } catch (error) {
    throw error;
  }
};
```

<br>
