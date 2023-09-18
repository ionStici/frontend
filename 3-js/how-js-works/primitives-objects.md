[&larr; Back](./README.md)

# Primitive and Reference Types

_Primitives and Reference (objects) data types._

- JavaScript Primitive Data Types: (1) Number, (2) String, (3) Boolean, (4) Undefined, (5) Null, (6) Symbol, (7) BigInt

- Everything else are basically: Objects

When we talk about memory and memory management, because of the different ways in which they are stored in memory, we call the: **primitives = primitive types** and then **Objects = Reference types**.

JavaScript engine has 2 components, the call stack and the heap:

- **Primitive types** _are stored in the call stack_, directly in the execution context in which they are declared.
- **Reference types** _are stored in the heap_.

<br>

## Primitive Types

```js
let age = 30;
let oldAge = age;
age = 31;

console.log(age); // 31
console.log(oldAge); // 30
```

**Declaring a variable** -> JS creates an identifier using the variable name -> the identifier will point to a certain newly created memory address e.g. `0001` -> the value will be stored in memory at the specified address.

The variable identifier `age` is equal to the allocated memory address `0001`, which holds the value of `30`.

On the next line we declare `oldAge` to be equal to `age`, and so `oldAge` will point to the same memory address as the `age` variable.

**Node:** a value at a certain memory address is immutable. From our example, if the value `30` is stored at the address `0001`, it will remain like this.

Next, we reassign `age` to `31`. Based on the rule above, a new piece of memory address `0002` is created and the `age` identifier now will point to this new created address, which is holding the new value of `31`.

Now, `age` is `31`, and `oldAge` is `30`.

<br>

## Reference Values

```js
const me = {
  name: "John",
  age: 30,
};

const friend = me;
friend.age = 27;

console.log(friend);
console.log(me);
```

When a new object is created, it is stored in the **heap**, here as well, we have a memory address `D30F` associated to the value. In the case of reference values, the identifier does not point directly to the newly created memory address from the heap.

Instead, the identifier will point to a new piece of memory address created in the call stack, which in turn will point to the object's memory address from the heap.

The memory address from the call stack, has a reference to the memory address in the heap which holds the object, this is why we call objects: **reference types** in this context.

It works this way because objects might be too large to be stored in the call stack, instead they are stored in the heap, which is specifically designed for memory management.

The stack just keeps a reference to where the object is stored in the heap, so that it can find it whenever necessary.

<br>

In our code example, we create a `friend` variable and set it equal to the `me` object. Just like with primitive values, the `friend` identifier will point to the exact same memory address as the `me` identifier. This memory address, again, contains the reference to the object from the heap. Now the `friend` object is essentially the exact same object as the `me` object, it results in one single object with 2 identifiers.

On the next line, using the `friend` identifier we change the object's `age` property. The object is found in the heap, and `30` is changed to `27`.

Now, when we log the `age` property we see `27` in both objects, even though we never changes `me.age` directly.

<br>
