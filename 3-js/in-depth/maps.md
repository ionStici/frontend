[&larr; Back](./README.md)

# Maps

**Map** - key / value pairs data structure. In maps, the key can be any data type.

Create an empty map, then fill up the map using the `set()` method by passing 2 arguments: the key and the value.

The `set()` method returns the updated map, and due to this we can chain the methods.

```js
const map1 = new Map(); // Map(0) {}
map1.set("name", "John");
map1.set(1, "Hello").set(true, "Happy");
// Map(3) {'name' => 'John', 1 => 'Hello', true => 'Happy'}
```

_Another way of populating a new map:_

```js
const map2 = new Map([
  [1, "JavaScript"],
  [2, "TypeScript"],
  [3, "Python"],
]);
```

An array with multiple arrays containing key / value pairs.

<br>

## Map Methods

```js
// 1. read data from a map using keys
map1.get("name"); // "John"

// 2. check if the map contains a certain key
map1.has(true); // true

// 3. delete elements based on keys
map1.delete(true);

// 4. get the size of the map
map1.size; // 2

// 5. delete all elements
map1.clear();
```

<br>

## Converting Objects to Maps

```js
const map3 = new Map(Object.entries(obj));
```

The structure of a map (arrays of arrays) is exactly the same array structure that is returned from calling `Object.entries()`, and due to this, we can convert objects to maps.

### Converting back map to arrays

```js
[...map1]; // array with key/value pair arrays
// [...map1.entries()]; // array with key/value pair arrays
[...map1.keys()]; // array with map keys
[...map.values()]; // array with map values
```

<br>

## Iterating Maps

Maps are iterables.

```js
for (const [key, value] of map2) console.log(`${key}: ${value}`);
```

Here, we directly destructure each item of the map into `[key, value]`.

<br>
