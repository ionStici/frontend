[&larr; Back](./README.md)

# Working with Dates

The dates we create using the `new Date()` constructor function are just another type of object. Therefore, they have their own methods that we can use to get or set components of a date.

_Creating a date object named `future`:_

```js
const future = new Date(2030, 10, 20, 15, 20);
// Wed Nov 20 2030 15:20:00 GMT+0200 (Eastern European Standard Time)
```

_Date methods:_

```js
future.getFullYear(); // 2030
future.getMonth(); // 10 | zero based
future.getDate(); // 20 | date of the month
future.getDay(); // 3 | day of the week, 3 = Wednesday | Sunday = 0 to Saturday = 6
future.getHours(); // 15
future.getMinutes(); // 20
future.getSeconds(); // 0
```

<br>

## Set components of a date

Equivalent date methods of the above versions.

```js
future.setFullYear(2040);
future.setMonth(11);
future.setDate(15);
future.setHours(13);
future.setMinutes(30);
future.setSeconds(0);
```

These methods also perform autocorrection.

## Get Date String

```js
future.toISOString(); // 2030-11-20T13:20:00.000Z
```

This is how to convert and store dates.

## Get the timestamp of a date

```js
future.getTime(); // 1921411200000
new Date(1921411200000); // Wed Nov 20 2030 15:20:00
```

We can get the timestamp of a date using `getTime()` method.

Then, we can convert the timestamp back to the date object.

## Present timestamp

```js
const present = Date.now(); // 1695805390496
```

<br>
