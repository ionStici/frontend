[&larr; Back](./README.md)

# Animations

## Table of Content

- [Keyframe](#keyframe)
- [Animation Duration](#animation-duration)

<br>

## Keyframe

**Keyframes** are a mechanism for assigning animation states to timestamps, along a timeline.

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

### animation-timing-function

```scss
.my-element {
  animation-timing-function: ease-in-out; // cubic-bezier(0.42, 0, 0.58, 1) | steps(10, end)
}
```

**Keywords:** linear, ease, ease-in, ease-out, ease-in-out.

We can [**define bezier curve**](https://cubic-bezier.com/#.17,.67,.83,.67) using the **`cubic-bezier()`** function, which accepts four number values. These values plot each part of the curve along the X and Y axis.

**`steps()`** easing function - break the timeline into defined, equal intervals. The _first argument_ is how many steps. The _second argument_ is the direction.

### animation-iteration-count

<br>
