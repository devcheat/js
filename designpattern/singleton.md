**singleton `class`**
===

> In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system

There are times when you need to create global objects across the applications. Specifically, you need objects that are instantiated only once during the lifetime of the whole request. For example, it could be a database connection object that you want to keep global across the whole request, since there’s no need to create multiple database objects per request. In such cases, the singleton pattern is really useful, as it guarantees that only a single copy of an object will be instantiated.

```js
class singletonClass {
  constructor(conString) {
      this.conString = conString
  }

  static Instance(conString) {
    if (!this.instance) {
      this.instance = new singletonClass(conString);
    }

    return this.instance;
  }
}

let con1 = singletonClass.Instance('mysqldb1');
let con2 = singletonClass.Instance('mysqldb2');

//the connections are the same
console.log("con1: "+con1.conString);
console.log("con2: "+con2.conString);
```
---
