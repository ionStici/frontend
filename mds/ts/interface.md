# Interfaces

## Table of Contents

- [Interfaces vs. Type Aliases](#interfaces-vs-type-aliases)
- [Interfaces and Classes](#interfaces-and-classes)
- [Deep Types](#deep-types)
- [Composed Interfaces](#composed-interfaces)
- [Extending Interfaces](#extending-interfaces)
- [Index Signatures](#index-signatures)
- [Optional Type Members](#optional-type-members)

## Interfaces vs. Type Aliases

Both `type` and `interface` can be used to type objects, but they have some differences:

- `interface` is specifically designed for typing objects and is often used in OOP due to its capabilities like extending and implementing.
- `type` is more versatile and can be used to type objects, primitives, unions, and more.

```ts
type User = {
  name: string;
};

const user: User;
```

```ts
interface User {
  name: string;
}

const user: User;
```

The `interface` syntax does not require an equals sign `=` before the typed object.

## Interfaces and Classes

You can apply an interface to a class using the `implements` keyword, ensuring the class adheres to the structure defined by the interface:

```ts
interface Robot {
  identify: (id: number) => void;
}

class OneSeries implements Robot {
  identify(id: number) {}
}
```

The `implements` keyword ensures that `OneSeries` conforms to the `Robot` interface.

## Deep Types

TypeScript allows interfaces to include deeply nested objects:

```ts
interface Robot {
  about: {
    general: {
      id: number;
      name: string;
    };
  };
  getRobotId: () => string;
}
```

## Composed Interfaces

You can compose interfaces by referencing other interfaces within them:

```ts
interface Version {
  version: number;
}

interface General {
  id: number;
  name: string;
  version: Version;
}

interface About {
  general: General;
}
```

This allows for cleaner, more readable code and reusability of smaller interfaces.

## Extending Interfaces

Interfaces can inherit properties from other interfaces using the `extends` keyword:

```ts
interface Color {
  color: string;
}

interface Width {
  width: number;
}

interface Button extends Color, Width {
  text: string;
}

let button: Button = {
  text: "Click",
  color: "red",
  width: 120,
};
```

The `Button` interface extends the `Color` and `Width` interfaces, inheriting all their properties.

## Index Signatures

When you don’t know the exact property names but know the structure, you can use index signatures:

```ts
interface SolarEclipse {
  [latitude: string]: boolean;
}

let eclipse: SolarEclipse = {
  "40.712776": true,
};
```

The `[latitude: string]: boolean` syntax allows for any string property name with a boolean value.

## Optional Type Members

You can make certain properties optional in an interface by using the `?` operator:

```ts
interface User {
  name: string;
  age?: number;
}

let user: User = {
  name: "Mike",
};
```
