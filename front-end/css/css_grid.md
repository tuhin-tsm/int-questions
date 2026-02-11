### CSS Grid

CSS Grid Layout is a two-dimensional grid-based layout system. With CSS Grid, you can define rows and columns, and place items into specific grid areas, making it ideal for larger scale layouts.

#### Terminology

**Grid Container** is the parent element that has `display: grid;` or `display: inline-grid;` applied to it. It establishes a new grid formatting context for its children.

**Grid Items** are the direct children of a grid container. They can be placed into specific grid cells or areas defined by the grid container.

```html
<div class="container">
  <div class="item item-1"></div>
  <div class="item item-2"></div>
  <div class="item item-3"></div>
</div>
```

**Grid Lines** are the dividing lines that make up the structure of the grid. They can be vertical (columns) or horizontal (rows). Grid lines are numbered starting from 1 at the top-left corner, with negative numbers counting backward from the end of the grid.

**Grid Tracks** are the space between two adjacent grid lines. They can be rows or columns.

**Grid Cells** are the individual units of the grid formed by the intersection of a row and a column.

**Grid Areas** are rectangular areas that consist of one or more grid cells. You can name grid areas and place items into them.

[Grid Terminology YT Video](https://www.youtube.com/watch?v=0m5qgfX2TVQ)
[CSS Tricks](https://css-tricks.com/complete-guide-css-grid-layout/)
[Grid in 13 Mins](https://www.youtube.com/watch?v=EiNiSFIPIQE)

### Parent container properties

`display: grid;` — Defines a grid container.
`grid-template-columns:` Defines the number and size of columns in the grid. Values can be specified in various units (px, %, fr, etc.) or using keywords like `auto` and `minmax()`. Example: `grid-template-columns: 200px 1fr 2fr;`

Fractional units (fr) represent a fraction of the available space in the grid container. For example, `1fr` means one part of the available space, while `2fr` means two parts.

`grid-template-rows:` Defines the number and size of rows in the grid. Similar to `grid-template-columns`. Example: `grid-template-rows: auto 100px 1fr;`
`grid-template-areas:` Defines named grid areas for easier placement of items. Example:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: auto 100px;
  grid-template-areas:
    "header header header"
    "sidebar content aside";
  /* We defined 3 columns and 2 rows.
    We defined 2 single quotes because we have 2 rows.
    We have 3 names in each single quote because we have 3 columns.
    The first row is named "header" and spans all 3 columns.
    The second row has 3 different names for each column. */
}
/* container defines the grid structure and the names of the areas. */
/* We can then place items into those areas using the grid-area property. */
.item-1 {
  grid-area: header; /* This item will be placed in the "header" area. */
}
.item-2 {
  grid-area: sidebar; /* This item will be placed in the "sidebar" area. */
}
```

`grid-gap:` Sets the size of the gutters (spacing) between rows and columns. Example: `grid-gap: 10px 20px;` (row-gap column-gap)
`justify-items:` Aligns grid items along the row (inline) axis within their grid area. Values: `start | end | center | stretch;`
`align-items:` Aligns grid items along the column (block) axis within their grid area. Values: `start | end | center | stretch;`
`justify-content:` Aligns the entire grid along the row (inline) axis within the grid container. Values: `start | end | center | stretch | space-between | space-around | space-evenly;`
`align-content:` Aligns the entire grid along the column (block) axis within the grid container. Values: `start | end | center | stretch | space-between | space-around | space-evenly;`
`grid-auto-rows:` Specifies the size of rows that are created automatically when content is placed outside the defined grid. Example: `grid-auto-rows: 100px;`
`grid-auto-columns:` Specifies the size of columns that are created automatically when content is placed outside the defined grid. Example: `grid-auto-columns: 200px;`
`grid-auto-flow:` Controls how auto-placed items are inserted into the grid. Values: `row | column | dense | row dense | column dense;`

### Child item properties

### Keywords for positioning

**span** — Used to make an item span multiple rows or columns.
**auto-fit** — Automatically fit as many columns or rows as possible within the container.
**auto-fill** — Automatically fill the row or column with as many items as possible, even if it means leaving empty spaces.
**minmax(min, max)** — Defines a size range for a track, where min is the minimum size and max is the maximum size. Example: `grid-template-columns: minmax(100px, 1fr);` (the column will be at least 100px but can grow to fill available space).
