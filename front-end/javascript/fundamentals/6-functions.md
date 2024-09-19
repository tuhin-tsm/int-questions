### Function Declaration

```js
function sayHi() {
  alert("Hello");
}
```

### Function Expression

```js
let sayHi = function () {
  alert("Hello");
};
```

_A Function Expression is created when the execution reaches it and is usable only from that moment._

### Function is a value

Let’s reiterate: no matter how the function is created, a function is a value. Both examples above store a function in the sayHi variable.

### Arrow functions

It doesn't have its own `this`, it's taken from outside. Also it means, they can't be used as constructors. They can't be called with new.

Arrows have no “arguments” variable.
