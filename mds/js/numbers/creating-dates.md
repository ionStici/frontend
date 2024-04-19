[&larr; Back](./README.md)

# Creating Dates

_Four ways of creating dates in JavaScript - using the `new Date()` contructor function._

Note: These methods perform autocorrection.

### 1. new Date

_No argumen. Get the current date and time:_

```js
const now = new Date(); // Wed Sep 27 2023 11:29:48 GMT+0300
```

### 2. Parsing the date from a date string

_Simple Date string:_

```js
new Date("Jane 22 2022");
// Sat Jan 22 2022 00:00:00 GMT+0200 (Eastern European Standard Time)
```

_Writing the string ourselves:_

```js
new Date("December 24, 2015");
// Thu Dec 24 2015 00:00:00 GMT+0200 (Eastern European Standard Time)
```

_Date string created by JavaScript:_

```js
new Date("2019-11-18T21:31:17.178Z");
// Mon Nov 18 2019 23:31:17 GMT+0200 (Eastern European Standard Time)
```

### 3. Parsing Date Arguments

Year -> Month -> Day -> Hour -> Minute -> Second

```js
new Date(2030, 10, 20, 15, 23, 5);
// Wed Nov 20 2030 15:23:05 GMT+0200 (Eastern European Standard Time)
```

Months in JS are zero based.

### 4. Parsing milliseconds

The amount of milliseconds passed since the biginning of the Unix time: **January 1, 1970**

```js
new Date(0);
// Thu Jan 01 1970 03:00:00 GMT+0300 (Eastern European Standard Time)
```

_Calculate 3 days after the Unix time:_

```js
new Date(3 * 24 * 60 * 60 * 1000); // calculating milliseconds
/// Sun Jan 04 1970 03:00:00 GMT+0300 (Eastern European Standard Time)
```

The number that we calculated is the **timestamp**.

<br>
