[&larr; Back](./README.md)

# Timers

## Table of Content

- [setTimeout](#settimeout)
- [setInterval](#setinterval)
- [Implementing a Countdown Timer](#implementing-a-countdown-timer)

<br>

## setTimeout

Timer that runs once after a defined time.

`setTimeout` runs in a non-blocking behavior.

```js
setTimeout(() => console.log("Hello"), 3 * 1000);
```

1. _Arg:_ a callback function
2. _Arg:_ An amount of time in milliseconds that will pass before the callback is executed.

### Arguments

```js
setTimeout((p1, p2) => console.log(`${p1}:${p2}`), 1000, "05", "15");
```

All the arguments that we pass after the delay will be used by the callback function as its arguments.

### Cancel the timer until the delay has passed

```js
const timer = setTimeout(() => console.log("Nope"), 1000);
clearTimeout(timer);
```

To clear a `setTimeout` timer:

1. First we store it in a variable
2. Then we pass that variable in the `clearTimeout()` function.

<br>

## setInterval

`setInterval` will call its callback every time in a time interval that we define.

```js
const intervals = setInterval(() => console.log("Hello"), 1000);
```

### Stop the setTimeout

```js
clearInterval(intervals);
```

### Exporting the callback

For the first time, `setInterval` will call the callback after the delay. If we want the callback to be called immediately, we can export the callback to a separate function and call it once outside and then rely on `setInterval`, sample code:

```js
const tick = () => "Hello";
tick();
setInterval(tick, 1000);
```

<br>

## Implementing a Countdown Timer

```js
const startTimer = function () {
  let time = 3; // 300 / 60 = 5 minutes

  const tick = function () {
    let minutes = String(Math.floor(time / 60)).padStart(2, "0");
    let seconds = String(Math.floor(time % 60)).padStart(2, "0");

    let timer = `${minutes}:${seconds}`;
    console.log(timer);

    time--;
    if (time < 0) stopTimer();
  };

  tick();
  const timer = setInterval(tick, 1000);
  const stopTimer = () => clearInterval(timer);
};

startTimer();
```

<br>
