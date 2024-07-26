[&larr; Back](./README.md)

# JSON

**JSON (JavaScript Object Notation)** is a language-independent standard format for storing and exchanging data between all programming languages (adopted by ECMA International).

JSON is used to facilitate data transfer in web applications between a client and a server.

Example: when we complete a web form, the data is converted from HTML to JavaScript objects to JSON objects and sent to a remote server for processing.

## Table of Contents

- [JSON Syntax Rules](#json-syntax-rules)
- [JSON Data Types](#json-data-types)
- [Reading a JSON String with JavaScript](#reading-a-json-string-with-javascript)
- [Writing a JSON String](#writing-a-json-string)

## JSON Syntax Rules

```json
{
  "person": {
    "name": "John",
    "age": 25
    "skills": ["HTML", "CSS"],
  }
}
```

- Curly braces for objects `{}`
- Square brackets for arrays `[]`
- Data is stored in name-value paits separated by a colon `:`
- Commas `,` for separating items. NO trailing commas.
- JSON property names MUST be in double-quoted `""`

Since JSON is derived from the JavaScript programming language, its appearance is similar to that of JavaScript objects.

## JSON Data Types

- String (double-quoted)
- Number (integer or floating point)
- Object (name-value pair)
- Array (comma-delimited)
- Boolean (true or false)
- null

Other data types that JSON doesn't cover (e.g. dates), can be stored as a string and then converted to the langauge-specific data structure.

## Reading a JSON String with JavaScript

In a typical web application, the JSON data that we receive from a web request comes in the form of a string.

At other times, JSON data is stored in a `.json` file (extention) that is used for authentication, configuration, or database storage.

In either case, we will need to convert the string to a format that we can use in order to access its parts.

Each programming language has its own mechanism to handle this conversion.

In JavaScript we have a built-in `JSON` class with a method called `.parse()` that takes a JSON string as a parameter and returns a JavaScript object.

_Converting a JSON string object into a JavaScript object:_

```js
const jsonData =
  '{ "book": { "name": "JSON Primer", "price": 29.99, "inStock": true, "rating": null } }';

const javaScriptObject = JSON.parse(jsonData);
```

## Writing a JSON String

Before we can send off our data across the web, we need to convert them to a JSON string.

In JavaScript we use the built-in `JSON` class method `stringify()` to transform JS objects to a JSON object.

```js
const jsonData = JSON.stringify(data);
```
