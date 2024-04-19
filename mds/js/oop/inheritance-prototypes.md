[&larr; Back](./README.md)

# Inheritance

## Table of Content

- [Inheritance: Constructor Functions](#inheritance-constructor-functions)
- [Inheritance: Object.create()](#inheritance-objectcreate)

<br>

## Inheritance: Constructor Functions

Student Class (child class) inherits from Person Class (parent class).

This will allow the child class to have access to specific properties and methods declared in the parent class.

This will work by setting up prototypal inheritance between two constructor functions.

```js
const Person = function (name, age) {
  this.name = name;
  this.age = age;
};

Person.prototype.sayHello = function () {
  console.log(`Hello, I'm ${this.name}`);
};

const Student = function (name, age, course) {
  Person.call(this, name, age);
  this.course = course;
};

// Linking prototypes
Student.prototype = Object.create(Person.prototype);

Student.prototype.myCourse = function () {
  console.log(`I'm studying ${this.course}`);
};

const john = new Student("John", 25, "Computer Science");

Student.prototype.constructor = Student;
```

The `call()` method from the `Student` class will call the `Person` function and will specify the `this` keyword to the newly empty object created by the new operator of the `john` object. It is this step where `Student` class "inherits" the parent class properties (e.g. `name` `age`).

By implementing **Inheritance**, we want the `Student` and `Person` classes to be connected, so that all instances of `Student` class get access to the methods from the `Person` prototype through prototype chain.

We can achive this by making `Person.prototype` the prototype of `Student.prototype`, using `Object.create()`

```js
Student.prototype = Object.create(Person.prototype);
```

**Note:** We have to make this connection of linking prototype with `Object.create()` before we add any methods to the prototype object of Student (child class), because at this point after using `Object.create()`, the prototype of `Student` will be empty, any previously declared methods will be overridden by `Object.create()` which returns an empty object. Then, onto that empty object we can add methods.

After linking prototypes, `Student.prototype` object inherits `Person.prototype`. We can use methods like `sayHello` from the `Person.prototype` on all instances of the `Student` class, we are effectively doing a method lookup, JavaScript trying to find the requested method in the prototype chain.

With ES6 Classes it works exactly the same internally, all that changes is the syntax.

```js
john.__proto__.__proto__.__proto__.__proto__;
// Student.prototype -> Person.prototype -> Object.prototype -> null

john instanceof Student; // true
john instanceof Person; // true
john instanceof Object; // true
```

`Student` is the constructor functions of `john`. In case of `Person` and `Object` that is also true, because we linked the prototypes together.

```js
Student.prototype.constructor; // Person object
```

This points back to Person, JavaScript thinks that the constructor of `Student.prototype` is `Person`. The reason for this is that we set the prototype property of `Student` using `Object.create()`. We need to fix this because sometimes it's important to rely on this `constructor` property, solution:

```js
Student.prototype.constructor = Student; // Student object
```

<br>

## Inheritance: Object.create()

```js
const PersonProto = {
  init(name, age) {
    this.name = name;
    this.age = age;
  },

  sayHello() {
    console.log(`Hello, I'm ${this.name}`);
  },
};

const StudentProto = Object.create(PersonProto);

StudentProto.init = function (name, age, course) {
  PersonProto.init.call(this, name, age);
  this.course = course;
};

StudentProto.myCourse = function () {
  console.log(`I'm Studying ${this.course}`);
};

const john = Object.create(StudentProto);
john.init("John", 25, "Computer Science");
// john.sayHello; john.myCourse;
```

<br>

- First, using `Object.create()` we create an object `StudentProto` linked to `PersonProto.prototype`.
- So `PersonProto.prototype` is the parent prototype of `Student.prototype`.
- `StudentProto` inherits from `PersonProto`, establishing the parent-child relationship.
- Then, using the `call` method on `PersonProto.init`, we define the `init` method for `StudentProto`.

<div></div>

- Then, we create other object instances from `StudentProto` using `Object.create()`.
- `john` is an instance of `StudentProto`.
- `StudentProto` is the prototype of `john`, and `PersonProto` in turn is the prototype of `StudentProto`.
- `john` instance inherits from `StudentProto`, which in turn inherits from `PersonProto`.
- `john` will be able to use all the methods from `StudentProto` and `PersonProto`.

<br>
