**ECMAScript 2009 `ES5`**
===

ECMAScript 2009, also known as ES5, was the first major revision to JavaScript.

## `use strict`
The `use strict` Directive
`use strict` defines that the JavaScript code should be executed in `strict mode`.

With strict mode you can, for example, not use undeclared variables.

- You can use strict mode in all your programs. It helps you to write cleaner code, like preventing you from using undeclared variables.
- `use strict` is just a string expression. Old browsers will not throw an error if they don't understand it.

```js
Using a variable, without declaring it, is not allowed:

"use strict";
x = 3.14;                // This will cause an error
```

## String[number] access
Property Access on Strings
The charAt() method returns the character at a specified index (position) in a string:

Example
```js
var str = "HELLO WORLD";
str.charAt(0);            // returns H
```
ES5 allows property access on strings:

Example
```js
var str = "HELLO WORLD";
str[0];                   // returns H
```
## Multiline strings
> Strings Over Multiple Lines
ES5 allows string literals over multiple lines if escaped with a backslash:
Example
```js
"Hello \
Dolly!";
```

## String.trim()
The trim() method removes whitespace from both sides of a string.

Example
```js
var str = "       Hello World!        ";
alert(str.trim());
```

## Array.isArray()
The isArray() method checks whether an object is an array.

Example
```js
function myFunction() {
  var fruits = ["Banana", "Orange", "Apple", "Mango"];
  var x = document.getElementById("demo");
  x.innerHTML = Array.isArray(fruits);
}
```
## Array forEach()
The forEach() method calls a function once for each array element.

Example
```js
var txt = "";
var numbers = [45, 4, 9, 16, 25];
numbers.forEach(myFunction);

function myFunction(value) {
  txt = txt + value + "<br>";
}
```
## Array map()
This example multiplies each array value by 2:

Example
```js
var numbers1 = [45, 4, 9, 16, 25];
var numbers2 = numbers1.map(myFunction);

function myFunction(value) {
  return value * 2;
}
```
## Array filter()
This example creates a new array from elements with a value larger than 18:

Example
```js
var numbers = [45, 4, 9, 16, 25];
var over18 = numbers.filter(myFunction);

function myFunction(value) {
  return value > 18;
}
```
## Array reduce()
This example finds the sum of all numbers in an array:

Example
```js
var numbers1 = [45, 4, 9, 16, 25];
var sum = numbers1.reduce(myFunction);

function myFunction(total, value) {
  return total + value;
}
```
## Array reduceRight()
This example also finds the sum of all numbers in an array:

Example
```js
var numbers1 = [45, 4, 9, 16, 25];
var sum = numbers1.reduceRight(myFunction);

function myFunction(total, value) {
  return total + value;
}
```
## Array every()
This example checks if all values are over 18:

Example
```js
var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.every(myFunction);

function myFunction(value) {
  return value > 18;
}
```
## Array some()
This example checks if some values are over 18:

Example
```js
var numbers = [45, 4, 9, 16, 25];
var allOver18 = numbers.some(myFunction);

function myFunction(value) {
  return value > 18;
}
```
## Array `indexOf()`
Search an array for an element value and returns its position.

Example
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.indexOf("Apple");
```

## Array lastIndexOf()
`lastIndexOf()` is the same as `indexOf()`, but searches from the end of the array.

Example
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var a = fruits.lastIndexOf("Apple");
```

## JSON.parse()
A common use of JSON is to receive data from a web server.

Imagine you received this text string from a web server:
```js
'{"name":"John", "age":30, "city":"New York"}'
```
The JavaScript function `JSON.parse()` is used to convert the text into a JavaScript object:
```js
var obj = JSON.parse('{"name":"John", "age":30, "city":"New York"}');
```

## JSON.stringify()
A common use of JSON is to send data to a web server.

When sending data to a web server, the data has to be a string.

Imagine we have this object in JavaScript:
```js
var obj = {name:"John", age:30, city:"New York"};
```
Use the JavaScript function `JSON.stringify()` to convert it into a string.
```js
var myJSON = JSON.stringify(obj);
```
## Date.now()
returns the number of milliseconds since zero date (January 1. 1970 00:00:00 UTC).

Example
```js
var timInMSs = Date.now();
```
`Date.now()` returns the same as `getTime()` performed on a Date object.

## Date `toISOString()`
The `toISOString()` method converts a Date object to a string, using the ISO standard format:

Example
```js
const d = new Date();
document.getElementById("demo").innerHTML = d.toISOString();
```
## Date `toJSON()`
`toJSON()` converts a Date object into a string, formatted as a JSON date.

JSON dates have the same format as the ISO-8601 standard: YYYY-MM-DDTHH:mm:ss.sssZ:

Example
```js
d = new Date();
document.getElementById("demo").innerHTML = d.toJSON();
```
## Property getters and setters
ES5 lets you define object methods with a syntax that looks like getting or setting a property.

This example creates a setter and a getter for the language property:

Example
```js
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "NO",
  get lang() {
    return this.language;
  },
  set lang(value) {
    this.language = value;
  }
};

// Set an object property using a setter:
person.lang = "en";

// Display data from the object using a getter:
document.getElementById("demo").innerHTML = person.lang;
```
## Reserved words as property names
ES5 allows reserved words as property names:

Object Example
```js
var obj = {name: "John", new: "yes"}
```
## Object methods
ES5 added a lot of new Object Methods to JavaScript:

Managing Objects
```js
// Create object with an existing object as prototype
Object.create(parent, donor)

// Adding or changing an object property
Object.defineProperty(object, property, descriptor)

// Adding or changing object properties
Object.defineProperties(object, descriptors)

// Accessing Properties
Object.getOwnPropertyDescriptor(object, property)

// Returns all properties as an array
Object.getOwnPropertyNames(object)

// Accessing the prototype
Object.getPrototypeOf(object)

// Returns enumerable properties as an array
Object.keys(object)
```
Protecting Objects
```js
// Prevents adding properties to an object
Object.preventExtensions(object)

// Returns true if properties can be added to an object
Object.isExtensible(object)

// Prevents changes of object properties (not values)
Object.seal(object)

// Returns true if object is sealed
Object.isSealed(object)

// Prevents any changes to an object
Object.freeze(object)

// Returns true if object is frozen
Object.isFrozen(object)
```
## Object defineProperty()
Object.defineProperty() is a new Object method in ES5.

It lets you define an object property and/or change a property's value and/or metadata.

Example
```js
// Create an Object:
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "NO",
};

// Change a Property:
Object.defineProperty(person, "language", {
  value: "EN",
  writable : true,
  enumerable : true,
  configurable : true
});

// Enumerate Properties
var txt = "";
for (var x in person) {
  txt += person[x] + "<br>";
}
document.getElementById("demo").innerHTML = txt;
```
Next example is the same code, except it hides the language property from enumeration:

Example
```js
// Create an Object:
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "NO",
};

// Change a Property:
Object.defineProperty(person, "language", {
  value: "EN",
  writable : true,
  enumerable : false,
  configurable : true
});

// Enumerate Properties
var txt = "";
for (var x in person) {
  txt += person[x] + "<br>";
}
document.getElementById("demo").innerHTML = txt;
```
This example creates a setter and a getter to secure upper case updates of language:

Example
```js
/// Create an Object:
var person = {
  firstName:"John",
  lastName : "Doe",
  language : "NO"
};

// Change a Property:
Object.defineProperty(person, "language", {
  get : function() { return language },
  set : function(value) { language = value.toUpperCase()}
});

// Change Language
person.language = "en";

// Display Language
document.getElementById("demo").innerHTML = person.language;
```
## Function bind()
With the bind() method, an object can borrow a method from another object.

This example creates 2 objects (person and member).

The member object borrows the fullname method from the person object:

Example
```js
const person = {
  firstName:"John",
  lastName: "Doe",
  fullName: function () {
    return this.firstName + " " + this.lastName;
  }
}

const member = {
  firstName:"Hege",
  lastName: "Nilsen",
}

let fullName = person.fullName.bind(member);
```
## Trailing commas
ES5 allows trailing commas in object and array definitions:

Object Example
```js
person = {
  firstName: "John",
  lastName: " Doe",
  age: 46,
}
```
Array Example
```js
points = [
  1,
  5,
  10,
  25,
  40,
  100,
];
```
> **WARNING** JSON does not allow trailing commas.

---