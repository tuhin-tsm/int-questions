### Flexbox

The main idea behind the flex layout is to give the container the ability to alter its items’ width/height (and order) to best fill the available space.

Most importantly, the flexbox layout is direction-agnostic as opposed to the regular layouts (block which is vertically-based and inline which is horizontally-based).

**Note:** Flexbox layout is most appropriate to the components of an application, and small-scale layouts, while the Grid layout is intended for larger scale layouts. CSS flexbox is a one-dimensional layout method while CSS grid is a two-dimensional layout method.

### Two Axes

Main axis(default: horizontal), Cross axis(default: vertical).

### Flex Container (The Parent)

**display**: Defines a flex container; use flex for block-level or inline-flex for inline-level. Values: `flex, inline-flex`

**flex-direction:** Defines the main axis (row or column) and the direction items are placed. Values: `row(default), row-reverse, column, column-reverse`

**flex-wrap:** Determines if items should stay on one line or wrap onto multiple lines. Values: `nowrap(default), wrap, wrap-reverse`

**flex-flow:** A shorthand for flex-direction and flex-wrap combined.

```css
.container {
  flex-flow: column wrap;
}
```

**justify-content:** Aligns items along the main axis (e.g., horizontal for rows).
Values: `flex-start(default) | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;`

**align-items:** Aligns items along the cross axis (e.g., vertical for rows).
Values: `stretch(default) | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;`

**align-content:** Aligns a flex container's lines within it when there is extra space in the cross-axis (only works with flex-wrap). When multiple lines of items exist, this property controls the spacing between those lines. Values: `stretch(default) | flex-start | flex-end | center | space-between | space-around | space-evenly | start | end + ... safe | unsafe;`

**gap:** Sets the size of the gutters (spacing) between items without using margins. It applies that spacing only between items not on the outer edges.

```css
gap: 10px;
gap: 10px 20px; /* row-gap column gap */
```

### Flex Items (The Children)

**order:** Controls the order in which items appear in the flex container (default is 0). `order: -1;` — Moves an item to the very beginning of the layout.

**flex-grow:** Sets how much an item will grow relative to the rest to fill available space. Default is 0 (do not grow). `flex-grow: 1;` — All items with flex-grow set to 1 will grow equally to fill the available space.

**flex-shrink:** Sets how much an item will shrink relative to the rest when space is tight. Default is 1 (shrink if necessary). `flex-shrink: 0;` — Prevents an item from shrinking when space is limited.

**flex-basis:** Sets the initial main size of an item before any space distribution occurs. Default is auto (size based on content). `flex-basis: 200px;` — Sets the initial size of the item to 200 pixels before growing or shrinking.

**flex:** The recommended shorthand for flex-grow, flex-shrink, and flex-basis combined. `flex: 1 0 200px;` — This means the item will grow to fill available space, will not shrink, and has an initial size of 200 pixels.

**align-self:** Allows an individual item to override the container's align-items value. Values: `auto(default) | flex-start | flex-end | center | baseline | stretch + ... safe | unsafe;`

### Interview "Cheat Sheet" Scenarios

1. **Centering an Item Both Horizontally and Vertically:**

```css
.container {
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  height: 100vh; /* Parent needs height */
}
```

2. What is the difference between `space-between` and `space-around`?

- `space-between`: Distributes items evenly with no space at the beginning or end. First item at the start, last item at the end, equal space in between.
- `space-around`: Distributes items evenly with equal space around each item (including at the beginning and end).

3. Why is `flex-basis` better than `width`?
   `flex-basis` is more flexible. If the `flex-direction` is `row`, it acts as `width`. If the `flex-direction` is `column`, it acts as `height`.
