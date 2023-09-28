[&larr; Back](./README.md)

# localStorage

[_Web Storage API_](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)

**`localStorage` API** - store data linked to a URL in the browser.

```js
const userName = "John";
const userData = { name: userName, age: 15 };

localStorage.setItem("userName", userName);
localStorage.setItem("userData", JSON.stringify(userData));

const retrieveUserName = localStorage.getItem("userName");
const retrieveUserData = JSON.parse(localStorage.getItem("userData"));

console.log(retrieveUserName); // John
console.log(retrieveUserData); // {name: 'John', age: 15}

localStorage.removeItem("userName");
localStorage.removeItem("userData");
```

**`localStorage.setItem()`** accepts 2 arguments. **Arg 1:** a reference key name. **Arg 2:** string we want to store.

**`localStorage.getItem()`** function to retrieve data. Pass in the associated key.

**`localStorage.removeItem("userName")`** remove items according to the associated key.

In case the data we want to store isn't a string, use **`JSON.stringify(data)`** to convert it to a string.

**`JSON.parse(localStorage.getItem("userData"))`** convert JSON back to a JavaScript object.

**Consider:** when retrieving objects from the local storage, the prototype chain is gone.

To see the data stored in the `localStorage`, go to: DevTools -> Application -> Local Storage -> Certain Link

<br>
