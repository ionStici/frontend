[&larr; Back](./README.md)

# Geolocation API

[_Geolocation Browser API_](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)

```js
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(
    (location) => {
      const { latitude, longitude } = location.coords;
      console.log([latitude, longiture]);
    },
    (error) => console.log(error.message)
  );
}
```

Using an `if` statement, we check if the browser provides the geolocation API (to avoid errors in old browsers).

`navigator.geolocation.getCurrentPosition()` function receives 2 callbacks.

1. The first callback will be called when the browser successfully receives the device's location data.

   The `location` parameter object contains location data, such as device coordinates.

2. The second callback is called when the browser cannot obtain the device's location data, for example because of setting restrictions.

_Create a Google maps link using the coordinates from the geolocation API:_

```js
`https://www.google.com/maps/@${latitude},${longitude}`;
```

<br>
