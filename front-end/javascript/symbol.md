# Symbol

Symbol is a built-in object whose constructor returns a symbol primitive — also called a Symbol value or just a Symbol — that's guaranteed to be unique.
Symbols are often used to add unique property keys to an object that won't collide with keys any other code might add to the object

```javascript
const symbol1 = Symbol();
const symbol2 = Symbol("description"); // optional description

// Uniqueness
const sym1 = Symbol("key");
const sym2 = Symbol("key");
console.log(sym1 === sym2); // Output: false
```

### Use Cases

1. Unique object properties

```javascript
const mySymbol = Symbol("mySymbol");
const obj = {
  [mySymbol]: "myValue",
};
console.log(obj[mySymbol]); // Output: 'myValue'
```

2. Constants

```javascript
const COLOR_RED = Symbol("red");
const COLOR_GREEN = Symbol("green");

function getColor(color) {
  switch (color) {
    case COLOR_RED:
      return "Red";
    case COLOR_GREEN:
      return "Green";
    default:
      return "Unknown color";
  }
}

console.log(getColor(COLOR_RED)); // Output: 'Red'
```
