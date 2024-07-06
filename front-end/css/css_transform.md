# CSS Transform

### Transform functions

1. **Translation**:

move an item around: `transform: translate(16px, 15px);`

In case of transform, critically the item's in-flow position doesn't change. From flow to flex to grid. For eg. the flexbox algorithm doesn't notice and keeps other children in the same place.

There's one thing that makes translate ridiculously powerful, though. Something totally unique in CSS language. When we use a _percentage_ value in translate, that percentage refers to the element's own size, not the available space within the parent container.

Setting `transform: traslateY(-100%)` moves the box up by its exact height.

2. **Scale**:
   allows to grow or shrink an element

Scale uses a unitless value that represents a multiple, similar to line-height. `scale(2)` means that the element should be 2x as big it would normally be.
We can also pass multiple values, to scale the x and y axis independently.

This reveals an important truth about transforms: elements are flattened into a texture(flat image).

3. **Rotate**:
   rotate our element. Default transform origin is the intersection of x and y.

```css
transform: rotate(90deg);
transform: rotate(0.5turn);
```

4. **Skew**:
   Skew can be useful for creating diagonal decorative elements.

```css
transform: skew(17deg);
transform: skewY(17deg);
```

### Transform origin

Every element has an origin, the anchor that the transform functions execute form.

```css
transform-origin: center;
transform-origin: left top;
```

### Combining multiple operations

We can string together multiple transform functions by space-separating them.
`transform: translateX(0px) rotate(0deg);`

**The order is important:** the transform functions will be applied sequentially. The transform functions are applied from right to left, like composition in functional programming.

### Inline elements

Transforms don't work with inline elements in Flow layout.
