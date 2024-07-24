**Storage API**
===

# The localStorage Object

- The localStorage object provides access to a local storage for a particular Web Site. It allows you to store, read, add, modify, and delete data items for that domain.

- The data is stored with no expiration date, and will not be deleted when the browser is closed.

- *The data will be available for days, weeks, and years.*

## The setItem() Method
The localStorage.setItem() method stores a data item in a storage.

It takes a name and a value as parameters:

**Example**
```js
localStorage.setItem("name", "John Doe");
```
## The getItem() Method
The localStorage.getItem() method retrieves a data item from the storage.

It takes a name as parameter:

**Example**
```js
localStorage.getItem("name");
```

# The sessionStorage Object
- The sessionStorage object is identical to the localStorage object.

- The difference is that the sessionStorage object stores data for one session.

- **The data is deleted when the browser is closed.**

**Example**
```js
sessionStorage.getItem("name");
```

## The setItem() Method
The sessionStorage.setItem() method stores a data item in a storage.

It takes a name and a value as parameters:

**Example**
```js
sessionStorage.setItem("name", "John Doe");
```
## The getItem() Method
The sessionStorage.getItem() method retrieves a data item from the storage.

It takes a name as parameter:

**Example**
```js
sessionStorage.getItem("name");
```
## The removeItem() Method
Syntax for REMOVING saved data from sessionStorage:
```js
sessionStorage.removeItem("key");
```
## The clear() Method
Syntax for REMOVING ALL saved data from sessionStorage:
```js
sessionStorage.clear();
```

