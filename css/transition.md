[&larr; Back](./README.md)

# CSS Transition

**CSS transition** can control the following four aspects of an element's transition:

1. The property
2. Duration
3. Delay
4. How the transition accelerates

<br>

## Table of Content

- [Transition](#transition)
- [Timing Function](#timing-function)
- [Delay](#delay)
- [Shorthand](#shorthand)
- [Combinations](#combinations)
- [all](#all)
- [Notes](#notes)

**Resources:**

- [MDN Using CSS transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
- [MDN Using CSS transforms](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transforms/Using_CSS_transforms)
- [CSS Transitions and Transforms for Beginners](https://thoughtbot.com/blog/transitions-and-transforms)

<br>

## Transition

```css
a {
  transition-property: color;
  transition-duration: 1s;
}

a:hover {
  color: red;
}
```

To create a transition, declare the `transition-property` and specify as value the _property name that you want to transition_.

Then, `transition-duration` will set the duration of the transition. Require seconds or milliseconds as value.

This will create a transition for the specified as value property.

[List of Animatable CSS Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)

The default value of duration is `0s`, or instantaneous, as if there is no transition.

<br>

## Timing Function

The timing function describes the pace of the transition. [by MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function)

```css
a {
  transition-timing-function: ease-out;
}
```

- `ease` (default value) starts the transition slowly, speeds up in the middle, and slows down again at the end.
- `ease-in` — starts slow, accelerates quickly, stops abruptly
- `ease-out` — begins abruptly, slows down, and ends slowly
- `ease-in-out` — starts slow, gets fast in the middle, and ends slowly
- `linear` — constant speed throughout

<br>

## Delay

```css
a {
  transition-delay: 1s;
}
```

Time to wait before startng the transition. Default value `0s`.

<br>

## Shorthand

```css
a {
  transition: color 0.25s ease-in 0.5s;
}
```

The properties must be specified in this order:

1. `transition-property`
2. `transition-duration`
3. `transition-timing-function`
4. `transition-delay`

Leaving out one of the properties causes the default value for that property to be applied.

One exception: You must set duration if you want to define delay. Since both are time values, the browser will always interpret the first time value as duration.

<br>

## Combinations

With the shorthand `transition` property, we can set separate transitions for multiple properties at once.

To add a new transition, add a comma `,` and then just set a second transition, code example:

```css
a {
  transition: color 0.25s ease-ing 0.3s, font-size 0.1s linear 0.3s;
  transition: all 0.25s;
}
```

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

## Notes

- The trick for fading out is using `opacity: 0`
- The transform property on hover or active will be in relation to the initial state.
- Transition will not work when `display: none` is applied.
- Animation and transition has been optimized by CSS for transform property.
- In several situation, for transition to work properly, you need to declare the initial state of the desired value

<div></div>

```css
.circle { opacity: 1; }
.circle.active { transition: all 1s: opacity .5 }
```

Set the transition on the active state if you only need the transition to work in one direction.
