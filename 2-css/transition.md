[&larr; Back](./README.md)

# CSS Transition

## Table of Content

- [transition shorthand](#transition-shorthand)
- [transition-property](#transition-property)
- [transition-duration](#transition-duration)
- [transition-timing-function](#transition-timing-function)
- [transition-delay](#transition-delay)
- [all](#all)
- [What can and can't transition](#what-can-and-cant-transition)
- [Different transitions for enter or exit](#different-transitions-for-enter-or-exit)
- [prefers-reduced-motion](#prefers-reduced-motion)
- [Performance considerations](#performance-considerations)
- [Notes](#notes)

<br>

## transition shorthand

`transition-property` -> `transition-duration` -> `transition-timing-function` -> `transition-delay`

```css
.btn {
  transition: transform 0.3s ease-in 0s, color 200ms;
}
```

We can declare multiple transitions in a comma-separated list.

Leaving out one of the properties causes the default value for that property to be applied.

_Exception:_ You must set duration if you want to define delay. Since both are time values, the browser will always interpret the first time value as duration.

<br>

## transition-property

Indicate which styles to transition for a particular property.

```css
.btn {
  transition-property: all;
}
```

The `transition-property` accepts one or more CSS property names in a comma-separated list.

<br>

## transition-duration

```css
.btn {
  transition-duration: 250ms;
}
```

Define the length of time that the transition will take to complete.

Here we define time units, either in seconds `s` or milliseconds `ms`. The default is `0s`.

<br>

## transition-timing-function

```css
.btn {
  transition-timing-function: linear; /* default */
}
```

Customize the speed of a CSS transition over the course of its duration.

Keywords: `linear ease ease-in ease-out ease-in-out`

Also we can use `steps` and `cubic`. We can use DevTools to experiment with different timing functions in real-time.

<br>

## transition-delay

```css
.btn {
  transition-delay: 150ms;
}
```

Specify the delay time for a transition.

<br>

## all

```css
a {
  transition: all 0.25s;
}
```

The `all` value can be used to apply the same values of transition to all properties of the target element.

This will enable the transition for all properties, and every value that changes will be transitioned in the same way.

<br>

## What can and can't transition

[List of Animatable CSS Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)

In general, it's only possible to transition elements that can have a "middle state" between their start and final states.

Common properties for transition: transform, colors, shadows, filters.

Pseudo-classes and events that can trigger state changes: `:hover :focus :target :active` and `class` change from JS.

<br>

## Different transitions for enter or exit

```css
.circle {
  opacity: 1;
  transition: opacity 1s;
}

.circle.active {
  opacity: 0.75;
  transition: opacity 0.5;
}
```

<br>

## prefers-reduced-motion

`prefers-reduced-motion` CSS media feature can detect if a user has indicated a preference for less motion from their device.

<br>

## Performance considerations

[Guide on high-performance CSS animations](https://web.dev/animations-guide/)

Use `transform` and `opacity` instead of `width` and `height` for transitions.

<br>

## Notes

- The trick for fading out is using `opacity: 0`
- The transform property on hover or active will be in relation to the initial state.
- Transition will not work when `display: none` is applied.
- Animation and transition has been optimized by CSS for `transform` property.
- Sometimes, for transition to work properly, you need to declare the initial state of the desired value.

<br>
