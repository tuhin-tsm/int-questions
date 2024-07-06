# Set

A Set is a built-in object which lets you store unique values of any type, whether primitive values or object references.
Unlike arrays, `set` objects ensure that no duplicate elements are added.

```javascript
const mySet = new Set();

// Adding values
mySet.add(1);
mySet.add(5);
mySet.add(1); // Duplicate value, will not be added
mySet.add("Hello");
mySet.add({ a: 1, b: 2 });

// Checking size
console.log(mySet.size); // Output: 4

// Checking presence
console.log(mySet.has(5)); // Output: true
console.log(mySet.has(2)); // Output: false

// Removing a value
mySet.delete(5);
console.log(mySet.size); // Output: 3

// Iterating over a Set
for (let item of mySet) {
  console.log(item);
}

// Clearing all values
mySet.clear();
console.log(mySet.size); // Output: 0
```

### Value equality

Value equality is based on the _SameValueZero_ algorithm. (It used to use SameValue, which treated 0 and -0 as different. Check browser compatibility.) This means NaN is considered the same as NaN (even though NaN !== NaN) and all other values are considered equal according to the semantics of the === operator.

### Performance

The `has` method, on average, faster than the `Array.prototype.includes` method when an array has a length equal to a set's size.
