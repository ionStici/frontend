[&larr; Back](./README.md)

# Top-Level await (ES2022)

**Top-Level await ES2022** - `await` keyword outside of `async` functions. Works only in modules.

```js
const response = await fetch("https://jsonplaceholder.typicode.com/posts");
const data = response.json();
console.log(data);
console.log("Hello");
// Promise - (1)
// Hello - (2)
```

`await` blocks the execution of the entire module, the `hello` string is logged only after the fetch is complete.

## top-level await useful example

```js
const getPost = async function () {
  const response = await fetch("https://jsonplaceholder.typicode.com/posts");
  const data = await response.json();
  return { title: data.at(-1).title, text: data.at(-1).body };
};

const post = getPost();
post.then((p) => console.log(p)); // post
```

_Instead of dealing `then` methods, we can make use of top-level `await`_

```js
const post = await getPost();
```

`post` will be the result of awaiting for the promise.

_Important implication of using top-level `await`:_ If one module imports a module which has a top-level `await`, then the importing module will wait for the exporting module to finish the blocking code. Only after the fetch is completed, we get the code from the importing module executed.

<br>
