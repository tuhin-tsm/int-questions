# CSS Transitions

By default, change in CSS happens instantaneously. In the blink of an eye, our button has teleported to a new position! This is incongruous with the natural world, where things happen gradually.

We can instruct the browser to interpolate from one state to another with the aptly-named `transition` property.

### The CSS transition is a shorthand property for:

- `transition-property`: CSS properties to which a transition effect is applied.
  ```css
  transition-property: margin-right, color;
  transition-property: all;
  ```
- `transition-duration`: length of time to complete the animation
  default: 0s
  ```css
  transition-duration: 6s;
  transition-duration: 250ms;
  ```
- `transition-timing-function`: how intermediate values are calculated
  ```css
  transition-timing-function: linear;
  transition-timing-function: ease-in;
  transition-timing-function: steps(6, end);
  ```
- `transition-delay`: the duration to wait before starting a property's transition effect
  `transition-delay: 250ms`
- `transition-behavior`

transition can take a number of values, but only two are required:

1. The name of the property we wish to animate
2. The duration of the animation

If you plan to animate multiple properties, you can pass it a comma-separated list:

```css
.btn {
  transition: transform 250ms, opacity 400ms;
}

.btn:hover {
  transform: scale(1.2);
  opacity: 0;
}
```

Animation is like salt: too much of it spoils the dish.

### Timing functions

A smooth animation should run at 60fps, which means we'll need to come up with 60 individual positions between start and end.

- **linear**: moves by the same amount each frame. liner is rarely the best choice.
- **ease-out**: comes charging in like a wild bull, but it runs out of energy. By the end it's like a sleepy turtle.
  When to use? Commonly used when something is entering from off-screen(eg. a modal appearing)
- **ease-in**: opposite of ease-out. It starts slow then speeds up.
  When to use? Something going beyond the bound of viewport.
- **ease-in-out**: It has equal amount of acceleration and deceleration. Most useful timing function.
- **Custom curves**: you can deifne your own custom easing curve, using the cubic bezier timing function.

```css
transition: transform 250ms cubic-bezier(0.1, 0.2, 0.3, 0.4);
```

### Animation performance

There are many things to consider, the absolutely-critical, need to know bits:

- Some CSS properties are wayy more expensive to animate that others. For example `height` is very expensive because it affects layout. When an element's height shrinks, it causes a chain reaction; all its siblings will also need to move up, to fill the space!
- Other properties, like `background-color`, are somewhat expensive to animate. They don't affect layout, but they do require a fresh coat of paint on every frame, which isn't cheap.
- Two properties - `transform` and `opacity` - are very cheap to animate.

### Hardware acceleration

The `will-change` CSS propery hints to browsers how an element is expected to change. Browsers may set up optimizations before an element is actually changed.
