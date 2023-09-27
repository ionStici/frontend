[&larr; Back](./README.md)

# Working with Dates

## Creating the Current Date

```js
const now = new Date();

const year = now.getFullYear();
const month = String(now.getMonth() + 1).padStart(2, "0");
const day = String(now.getDate()).padStart(2, "0");

const hours = now.getHours();
const minutes = now.getMinutes();
const seconds = now.getSeconds();

const currentDate = `${day}/${month}/${year}, ${hours}:${minutes}:${seconds}`;
// 27/09/2023, 12:15:34
```

<br>

## Storing and Creating a Date

```js
// STORING
const dates = [];
const now = new Date();
const nowISO = now.toISOString(); // 2023-09-27T09:17:38.057Z
dates.push(nowISO);
```

```js
// CREATING
const date = new Date(dates[0]); // Wed Sep 27 2023 12:18:36

const day = String(date.getDate()).padStart(2, "0");
const month = String(date.getMonth() + 1).padStart(2, "0");
const year = date.getFullYear();

const displayDate = `${day}/${month}/${year}`; // 27/09/2023
```

<br>

## Operating with Dates

Whenever we attempt to convert a date to a number, the result is gonna be the timestamp in milliseconds.

The timestamp difference between 2 dates will result in the elapsed time between these 2 dates.

```js
const now = +new Date(); // 1695808212730
Math.round(now / (24 * 60 * 60 * 1000));
// 19627 days passed since the Unix time
```

### Calculate the days passed between 2 dates

```js
const calcDaysPassed = (date1, date2) => {
  return Math.round(Math.abs(date1 - date2) / (24 * 60 * 60 * 1000));
};
calcDaysPassed(new Date(), new Date(2025, 0, 1)); // 462 (days)
```

Use `Math.round()` to remove the decimals, which represent time during the day.

If you need precise calculations, use a date library like moment.js

### Date formatter function

```js
const formatDate = function (date) {
  const calcDaysPassed = (date1, date2) => {
    return Math.round(Math.abs(date1 - date2) / (1000 * 60 * 60 * 24));
  };

  const daysPassed = calcDaysPassed(new Date(), date);

  if (daysPassed === 0) return "Today";
  if (daysPassed === 1) return "Yesterday";
  if (daysPassed <= 7) return `${daysPassed} days ago`;

  const day = String(date.getDate()).padStart(2, "0");
  const month = `${date.getMonth() + 1}`.padStart(2, "0");
  const year = date.getFullYear();

  return `${day}/${month}/${year}`;
};

formatDate(new Date(2023, 8, 25)); // 3 days ago
```

<br>
