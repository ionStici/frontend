[&larr; Back](./README.md)

# Sets

**Set** - a collection of unique values (no duplicates).

Inside the `Set()` function we pass an iterable, like an array or string.

```js
const uniqueNumbers = new Set([1, 2, 1, 3]);
console.log(uniqueNumbers); // Set(3) {1, 2, 3}
console.log(new Set("Hello")); // Set(4) {'H', 'e', 'l', 'o'}
```

After filling the set, it will remove the duplicates.

<br>

## Set Methods

```js
const mySet = new Set([1, 3, 5, 3]);

// 1. get the size of the set
mySet.size; // 3

// 2. check if the set contains a certain element
mySet.has(3); //true

// 3. add new elements
mySet.add(7);

// 4. delete elements
mySet.delete(7);

// 5. delete all the elements
mySet.clear();
```

How to retrieve a value from a set? The order of elements in sets is irrelevant, there are no indexes, we cannot directly get a value from a set. Instead, we can check whether a particular value is in a set or not using the `has()` method.

<br>

## Set use case

Sets are a great tool for removing duplicate values from arrays.

```js
const myArr = [1, 2, 3, 3]; // (4) [1, 2, 3, 3]
const mySet = new Set(myArr); // Set(3) {1, 2, 3}

console.log(myArr.length, mySet.size); // 4 3
const uniqueArr = [...mySet]; // (3) [1, 2, 3]
```

After creating a set from an array, we can convert the set back to array using the spread operator `...`

<br>

## Looping Sets

Sets are iterables.

```js
for (const item of mySet) console.log(item);
```

<br>
