# The event loop

JavaScript has a runtime model based on an event loop, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks.
This model is quite different from models in other languages like C and Java.

JavaScript is single-threaded, meaning it can only execute one task at a time in a single call stack. The event loop helps manage the execution of multiple tasks, including asynchronous operations, ensuring that non-blocking code can run effectively.

The event loop got its name because of how it's usually implemented, which usually resembles:

```javascript
while (queue.waitForMessage()) {
  queue.processNextMessage();
}
// queue.waitForMessage() waits synchronously for a message to arrive (if one is not already available and waiting to be handled).
```

A downside of this model is that if a message takes too long to complete, the web application is unable to process user interactions like click or scroll. The browser mitigates this with the "a script is taking too long to run" dialog. A good practice to follow is to make message processing short and if possible cut down one message into several messages.

### How it works

The event loop continuously checks the **call stack** and the **task queue (or message queue)** to determine what code to execute next.

1. **Call Stack:**

   When a function is invoked, it gets pushed onto the stack. When the function completes, it gets popped off the stack.

2. **Task Queue:**

   The task queue holds messages (tasks) that are waiting to be processed. These tasks come from various sources, such as user interactions (clicks, keyboard events), setTimeout, setInterval, Promises, or other asynchronous operations.

Example:

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");
```

#### Output

```shell
Start
End
Promise
Timeout
```

#### Execution Flow:

1. **Call Stack:** Initially, the `console.log('Start')` is pushed onto the stack and executed, printing "Start".
2. **Call Stack:** `setTimeout` is called, which sets up a timer for 0 milliseconds and places the callback in the task queue. The `setTimeout` function itself is removed from the stack.
3. **Call Stack:** A resolved Promise is created and the then callback is scheduled to run after the current script, adding it to the microtask queue. The Promise setup code is removed from the stack.
4. **Call Stack:** The console.log('End') is pushed onto the stack and executed, printing "End".

#### Visualization:

1. **Call Stack:** console.log('Start') → console.log('End')
2. **Task Queue:** setTimeout callback
3. **Microtask Queue:** Promise then callback

#### Microtask Queue vs. Task Queue:

**Microtasks (e.g., Promises)** have higher priority than regular tasks (e.g., `setTimeout`).
After the current synchronous code execution completes, microtasks are processed before the task queue.

### Zero delays

Zero delay doesn't mean the call back will fire-off after zero milliseconds. It indicates a minimum time — not a guaranteed time. The execution depends on the number of waiting tasks in the queue.
