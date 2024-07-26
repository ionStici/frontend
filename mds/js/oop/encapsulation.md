[&larr; Back](./README.md)

# Encapsulation

## Table of Contents

- [Protected Properties and Methods](#protected-properties-and-methods)
  - [Data privacy Convention](#data-privacy-convention)
- [Private Class Fields and Methods](#private-class-fields-and-methods)
  - [static fields](#static-fields)

<br>

## Protected Properties and Methods

**Encapsulation and Data privacy:** keeping some properties and methods private inside the class, so that they are not accessible from outside of the class. The rest of the methods are exposed as public interface (API).

_Why we need encapsulation and data privacy:_

1. To prevent code from outside of a class to accidentally manipulate data inside the class. We are not supposed to manually mess with properties directly, we should encapsulate it.
2. When we expose only a small interface (API), only a few public methods, then we can change all the other internal methods with more confidence, because in this case we can be sure that external code does not rely on these private methods, therefore our code will not break when we do internal changes.

### Data privacy Convention

Add an underscore `_` in front of property names.

```js
this._account = accoutn;
_verify() { return true; }
```

We can still access the property from outside the class, this is not truly private, just a convention. But at least now everyone on our team, including oruself, will know that this property is not supposed to be touched outside the class.

If we need to access a private proeprty from outside, we can implement a public method or a getter for that:

```js
getAccount() {
  return this._account;
}
```

Doing so, we can access private properties, but we cannot override them.

It is common to have a method called `get` or `set` instead of using a real getter or setter.

<br>

## Private Class Fields and Methods

Why **class fields**? In tradition OOP languages, properties are called **fields**.

With this new feature, JavaScript is moving away from the idea that classes are just syntactic sugar over constructor functions.

**4 different kinds of fields and methods (8 in total):**

```js
class Accoutn {
  // 1. Public fields (instances)
  locale = navigator.language;

  // 2. Private fields (instances)
  #pin;
  #data = [];

  constructor(name, pin) {
    this.name = name;
    this.#pin = pin;
  }

  // 3. Public methods
  getData() {
    return this.#data;
  }

  // 4. Private methods
  #approve(val) {
    return true;
  }
}
```

<br>

1. **Public instance fields**

   We can think of a field as a property that will be on all instances.

   `locale` is the public field, it will be on all instances created with this class.

   We don't pass any value into the constructor for this field, we just need `navigator.language` value for `locale` on all instances.

   Public fields are not on the prototype / they're reference-able by the `this` keyword.

   <br>

2. **Private fields:** the properties are not accessible from outside the class.

   - We use a hash `#` symbol before the field name.
   - Note: The hash `#` is part of the property name `#pin`.

   ```js
   console.log(acc1.#pin); // error
   ```

   We can't access the properties outside, they are truly private and no longer accessible.

   Instead, we access them using methods as the public API.

   We want to make the `pin` property private, and also set its value based on the input value of the constructor method, and because these private fields have to be out of the `constructor` or of any method, then we just set the `#pin` empty. This will be like creating an empty variable. In the beginning this `#pin` will be set to undefined, then in the constructor we re-define its value as usual.

   _Note:_ as with public fields, private fields are only available on the instances themselves, and not on the prototype, even if they are defined outside the `constructor` method.

<br>

3. **Public methods**

   All the class methods are the public interface (API) of our class.

<br>

4. **Private methods**

   Private methods are useful for hiding the implementation details from the outside.

   To make a method private: prepend the method with a hash `#` symbol.

<br>

### static fields

Besides these 4 features, there is also the **static** version of the same forms.

**static public methods:** adding the `static` keyword in front of the method.

```js
static helper() { console.log('help'); }
// static methods only work like this:
Account.helper(); // help
```

Static methods are available only on the class itself.

<br>
