[&larr; Back](./README.md)

# Inheritance Between ES6 Classes

ES6 Classes are a layer of abstraction over constructor functions.

The class syntax hides a lot of details that happens behind the scenes.

<br>

## Inheritance

With **inheritance** we can create a _parent class_ (superclass) with properties and methods that multiple _child classes_ (subclasses) share. The child classes inherit the properties and methods from their parent class.

```js
class PersonCl {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHello() {
    console.log(`Hello, I'm ${this.name}.`);
  }
}

class StudentCl extends PersonCl {
  constructor(name, age, course) {
    super(name, age);
    this.course = course;
  }

  sayHello() {
    console.log(`Hello, I'm ${this.name}.`);
    console.log(`I'm studying ${this.course}`);
  } // override methods of the parent class

  get name() {
    return this.name;
  }
}

const john = new StudentCl("John", 25, "Computer Science");
```

`StudentCl` class inherits from `PersonCl` class.

- The `extends` keyword will link the prototypes behind the scenes and establish the prototype chain. So it will make the methods of the parent class available to the child class.
- The `constructor()` will receive the same arguments as the parent class with some additional ones.
- Then, we call the `super()` method, which essentially is the `constructor` function of the parent class. So here we pass in the arguments for the `constructor` of the parent class.

The `super` method musted be called first in the constructor function, otherwise JavaScript will throw a reference error, this is because the call of the `super` method is responsible for creating the `this` keyword in the subclass.

**We can override methods of the parent class**. This works because the methods of a child class appears first in the prototype chain.

<br>
