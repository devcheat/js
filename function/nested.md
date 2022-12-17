JavaScript Nested Functions
===
- All functions have access to the global scope. In fact, in JavaScript, all functions have access to the scope "above" them.

> JavaScript supports nested functions. Nested functions have access to the scope "above" them.

In this example, the inner function plus() has access to the counter variable in the parent function:

Example
```js
function add() {
  let counter = 0;
  function plus() {
    counter += 1;
  }
  plus();   
  return counter;
}
```
---
