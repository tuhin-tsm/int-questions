# ES6 and Beyond

1. What is the difference between `let`, `const`, and `var` in JavaScript?

- `let` and `const` are block-scoped variables, while `var` is function-scoped. Hoisted to the top of its block but not initialized, leading to the temporal dead zone (TDZ).
- `let` allows reassignment, while `const` is a constant that cannot be reassigned.
- `var` has hoisting behavior, while `let` and `const` do not.

2. What are arrow functions in ES6?

- Arrow functions have a shorter syntax.
- They do not have their own this context; they inherit this from the parent scope (lexical scoping).
- Cannot be used as constructors (i.e., with new).

3. What is a template literal in ES6?

- Template literals are a way to concatenate strings in JavaScript using backticks (` `).
- They allow for easy interpolation of variables and expressions using `${}` syntax.
- Template literals also support multi-line strings without the need for escape characters.

4. What are destructuring assignments in ES6?

- Destructuring allows unpacking values from arrays or properties from objects into distinct variables.
-

```javascript
const [a, b] = [1, 2];
const { name, age } = { name: "John", age: 30 };
```

5. What is the spread operator in ES6?

- The spread operator (`...`) allows an iterable (e.g., an array or string) to be expanded into individual elements.
- It can be used to create copies of arrays, merge arrays, or pass multiple arguments to a function.

  ```javascript
  const arr1 = [1, 2, 3];
  const arr2 = [...arr1, 4, 5];
  ```

- Rest parameters (...) allow representing an indefinite number of arguments as an array.

  ```javascript
  function sum(...args) {
    return args.reduce((acc, curr) => acc + curr, 0);
  }
  console.log(sum(1, 2, 3)); // 6
  ```

6. What are the new features introduced in ES6?

- ES6 introduced several new features such as arrow functions, template literals, destructuring assignments, and the spread operator.
- It also added classes, modules, promises, and enhanced object literals.
- These features aimed to improve the syntax and functionality of JavaScript.

7. What are the new features introduced in ES6 for working with classes? Provide an example.

- ES6 introduced class syntax for defining classes, which includes class declarations, constructors, methods, and inheritance.

  ```javascript
  class Person {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }

    greet() {
      console.log(`Hello, my name is ${this.name}`);
    }
  }

  class Student extends Person {
    constructor(name, age, grade) {
      super(name, age);
      this.grade = grade;
    }

    study() {
      console.log(`${this.name} is studying`);
    }
  }

  const student = new Student("John", 20, "A");
  student.greet(); // Hello, my name is John
  student.study(); // John is studying
  ```

8. What are modules in JavaScript?

- Modules are a way to organize and encapsulate code in JavaScript.
- They allow you to split your code into separate files, each containing its own functionality.
- Modules can export and import functions, objects, or values to be used in other parts of your codebase.

9. How do Promises work in JavaScript? Provide an example of how to use a Promise.

- Promises represent the eventual completion (or failure) of an asynchronous operation and its resulting value.
- They have three states: pending, fulfilled, and rejected.

  ```javascript
  const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Success!"), 1000);
  });

  promise.then((result) => console.log(result)); // Success!
  ```

10. What is async/await and how does it simplify working with Promises? Provide an example.

- `async` functions return a Promise and use the `await` keyword to pause execution until the Promise resolves. The `await` keyword is permitted within `async` function body.
- It enables asynchronous, promise-based behavior to be written in a cleaner style and avoiding need to configure promise chains.

  ```javascript
  async function fetchData() {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  }

  fetchData();
  ```

11. What is the purpose of the Promise.all method? Provide an example of its use.

- Promise.all takes an array of Promises and returns a single Promise that resolves when all of the input Promises have resolved, or rejects if any Promise rejects.

  ```javascript
  const promise1 = Promise.resolve(3);
  const promise2 = 42;
  const promise3 = new Promise((resolve, reject) => {
    setTimeout(resolve, 100, "foo");
  });

  Promise.all([promise1, promise2, promise3]).then((values) => {
    console.log(values); // [3, 42, "foo"]
  });
  ```
