**ECMAScript 2017**
===

New Features in ECMAScript 2017
This chapter introduces the new features in ECMAScript 2017:

# JavaScript String padding
ECMAScript 2017 added two String methods: padStart and padEnd to support padding at the beginning and at the end of a string.

Examples
```js
let text = "5";
text = text.padStart(4,0);
let text = "5";
text = text.padEnd(4,0);
```
> JavaScript string padding is supported in all modern browsers since April 2017

# JavaScript Object `entries()`
ECMAScript 2017 added the `Object.entries()` method to objects.

`Object.entries()` returns an array of the key/value pairs in an object:

Example
```js
const person = {
  firstName : "John",
  lastName : "Doe",
  age : 50,
  eyeColor : "blue"
};

let text = Object.entries(person);
```
`Object.entries()` makes it simple to use objects in loops:

Example
```js
const fruits = {Bananas:300, Oranges:200, Apples:500};

let text = "";
for (let [fruit, value] of Object.entries(fruits)) {
  text += fruit + ": " + value + "<br>";
}
```
`Object.entries()` also makes it simple to convert objects to maps:

Example
```js
const fruits = {Bananas:300, Oranges:200, Apples:500};

const myMap = new Map(Object.entries(fruits));
```
# JavaScript Object `values()`
Object.values() are similar to Object.entries(), but returns a single dimension array of the object values:

Example
```js
const person = {
  firstName : "John",
  lastName : "Doe",
  age : 50,
  eyeColor : "blue"
};

let text = Object.values(person);
```
# JavaScript `async` and `await`
Waiting for a Timeout
```js
async function myDisplay() {
  let myPromise = new Promise(function(myResolve, myReject) {
    setTimeout(function() { myResolve("I love You !!"); }, 3000);
  });
  document.getElementById("demo").innerHTML = await myPromise;
}

myDisplay();
```
# JavaScript `Object.getOwnPropertyDescriptors`