### Label identifier for breaking/continuing from multiple nested levels of loops

```js
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    let input = prompt(`Value at coords (${i},${j})`, "");

    // if an empty string or canceled, then break out of both loops
    if (!input) break outer; // (*)

    // do something with the value...
  }
}

console.log("Done!");
```

### The "for..in" loop

To walk over all keys of an object, there exists a special form of the loop: `for..in`.

The syntax:

```js
for (key in object) {
  // executes the body for each key among object properties
}
```

Technically, because arrays are objects, it is also possible to use `for..in`.

### The "for..of" loop

The `for..of` doesn’t give access to the number of the current element, just its value, but in most cases that’s enough. And it’s shorter.

```js
for (let fruit of fruits) {
  console.log(fruit);
}
```

### A word about “length”

The length property automatically updates when we modify the array. To be precise, it is actually not the count of values in the array, but the greatest numeric index plus one.

```js
let fruits = [];
fruits[123] = "Apple";

console.log(fruits.length); // 124
```

Another interesting thing about the length property is that it’s writable.
