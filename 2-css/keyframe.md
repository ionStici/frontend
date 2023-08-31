[&larr; Back](./README.md)

# Animations

## Table of Content

- [Animation Guide | Web.Dev](https://web.dev/animations/)

<div></div>

- [Keyframe](#keyframe)
- [Animation Duration](#animation-duration)
- [animation-timing-function](#animation-timing-function)
- [animation-iteration-count](#animation-iteration-count)
- [animation-direction](#animation-direction)
- [animation-delay](#animation-delay)
- [animation-play-state](#animation-play-state)
- [animation-fill-mode](#animation-fill-mode)
- [The animation shorthand](#the-animation-shorthand)
- [prefers-reduced-motion](#prefers-reduced-motion)

<br>

## Keyframe

**Keyframes** are a mechanism for assigning animation states to timestamps along a timeline.

```scss
@keyframe my-animation {
  // from { transform: translateY(20px); }
  // to { transform: translateY(0); }
  0% {
    transform: translateY(20px);
  }
  75% {
    transform: translateY(30px);
  }
}
```

After the `@keyframe` keyword, we define a name for our animation that we reference when we use it.

Inside the keyframe rule, `from` and `to` are keywords that represent `0%` and `100%`, which are the start and end of the animation. With percentages, we can add as many positions as we like along the timeframe.

When we want to use the animation, we assign the keyframe identifier to the `animation-name` property inside the element selector we want to animate.

```css
.my-element {
  animation-name: my-animation;
}
```

_p.s._ We can assign multiple keyframes at-rules.

<br>

### Animation Duration

```scss
.my-element {
  animation-duration: 10s; // time value
}
```

How long the keyframe timeline should be.

<br>

### animation-timing-function

We can use timing functions that calculate the speed of an animation at each point.

```scss
.my-element {
  animation-timing-function: ease-in-out; // cubic-bezier(0.42, 0, 0.58, 1) | steps(10, end)
}
```

- **Keywords:** linear, ease, ease-in, ease-out, ease-in-out.

- We can [**define bezier curve**](https://cubic-bezier.com/#.17,.67,.83,.67) using the **`cubic-bezier()`** function, which accepts four number values. These values plot each part of the curve along the X and Y axis.

- **`steps()`** easing function - break the timeline into defined, equal intervals. The _first argument_ is how many steps. The _second argument_ is the direction.

<br>

### animation-iteration-count

```css
.el {
  animation-iteration-count: 10;
}
```

The `animation-iteration-count` property defines how many times the animation will run.

The `infinite` keyword value will loop the animation indefinitely.

<br>

### animation-direction

```css
.el {
  animation-direction: reverse;
}
```

Set which direction the timeline runs over your keyframes. Values:

- `normal` the default value, which is forwards.
- `reverse` runs backwards over your timeline.
- `alternate` for each animation iteration, the timeline will run forwards or backwards in sequence.
- `alternate-reverse` the reverse of `alternate`.

<br>

### animation-delay

```css
.el {
  animation-delay: 1.5s;
}
```

The `animation-delay` property defines how long to wait before starting the animation.

<br>

### animation-play-state

```css
.el {
  animation-play-state: paused;
}
```

The `animation-play-state` property allows you to play and pause the animation.

The default value is `running` and if you set it to `paused`, it will pause the animation.

<br>

### animation-fill-mode

```css
.el {
  animation-fill-mode: backwards;
}
```

The `animation-fill-mode` property defines which values in your `@keyframes` timeline persist before the animation starts or after it ends. The default value is `none` which means when the animation is complete, the values in your timeline are discarded.

- `forwards` The last keyframe will persist, based on the animation direction.
- `backwards` The first keyframe will persist, based on the animation direction.
- `both` follows the rules for both `forwards` and `backwards`.

<br>

### The animation shorthand

```css
.el {
  animation: my-animation 10s ease-in-out 1s infinite forwards forwards running;
}
```

Animation properties order:

1. `animation-name`
2. `animation-duration`
3. `animation-timing-function`
4. `animation-delay`
5. `animation-iteration-count`
6. `animation-direction`
7. `animation-fill-mode`
8. `animation-play-state`

<br>

### prefers-reduced-motion

Users can define in their operating system that they prefer to reduce motion experienced when they interact with applications and websites. This preference can be detected using the `prefers-reduced-motion` media query.

```css
@media (prefers-reduced-motion) {
  .my-autoplaying-animation {
    animation-play-state: paused;
  }
}
```

<br>
