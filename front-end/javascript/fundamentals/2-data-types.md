### Dynamically typed

JavaScript is dynamically typed language meaning that there exist data types, but variables are not bound to any of them.

Mathematical operations are "safe" in JavaScript. We can do anything: divide by zerp, treat non-numeric strings as numbers, etc. The script will never stop with a fatal error. At worst we will get `NaN` as the result.

### 8 basic data types

- Primitive data types(7)

  - number
  - bigint
  - boolean
  - null
  - undefined
  - symbol

- Non-primitive data type
  - object

### BigInt

Standard numbers range is `±(253-1)`.

A `BigInt` value is created by appending `n` to the end of an integer.

```javascript
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

### `null` and `undefined`

The special `null` and `undefined` value have their own data type and contains `null` and `undefined` respectively.

`null` represents "nothing", "empty" or "value unknown".
`undefined` represents "value not assigned".

### Objects and Symbols

Objects are used to store collections of data. The `symbol` type is used to create unique identifiers for objects.

### The typeof operator

It returns type of the operand. The result of `typeof null` is `"object"`. That's an officially recognized error in `typeof`, coming from very early days of JavaScript and kept for compatibility.
