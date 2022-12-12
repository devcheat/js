**Shared Worker**
===
- [**Shared Worker**](#shared-worker)
  - [Constructors `SharedWorker()`](#constructors-sharedworker)
  - [Instance properties](#instance-properties)
  - [`SharedWorker.port` Read only](#sharedworkerport-read-only)
  - [Events](#events)
  - [Instance methods](#instance-methods)
  - [Example](#example)

---
The SharedWorker interface represents a specific kind of worker that can be accessed from several browsing contexts, such as several windows, iframes or even workers. They implement an interface different than dedicated workers and have a different global scope, `SharedWorkerGlobalScope`.

> **Note:** If SharedWorker can be accessed from several browsing contexts, all those browsing contexts must share the exact same origin (same protocol, host and port).

## Constructors `SharedWorker()`
Creates a shared web worker that executes the script at the specified URL.

## Instance properties
Inherits properties from its parent, EventTarget.

## `SharedWorker.port` Read only
Returns a MessagePort object used to communicate with and control the shared worker.

## Events
`error`
Fires when an error occurs in the shared worker.

## Instance methods
Inherits methods from its parent, `EventTarget`.


## Example
In Shared Worker we have two HTML pages, each of which uses some JavaScript to perform a simple calculation. The different scripts are using the same worker file to perform the calculation — they can both access it, even if their pages are running inside different windows.

The following code snippet shows creation of a SharedWorker object using the `SharedWorker()` constructor. Both scripts contain this:
```js
const myWorker = new SharedWorker('worker.js');
```
Both scripts then access the worker through a MessagePort object created using the SharedWorker.port property. If the onmessage event is attached using addEventListener, the port is manually started using its `start()` method:
```js
myWorker.port.start();
```
When the port is started, both scripts post messages to the worker and handle messages sent from it using `port.postMessage()` and `port.onmessage`, respectively:
```js
const first = document.querySelector("#number1");
const second = document.querySelector("#number2");

const result1 = document.querySelector(".result1");

if (!!window.SharedWorker) {
  const myWorker = new SharedWorker("worker.js");

  first.onchange = function () {
    myWorker.port.postMessage([first.value, second.value]);
    console.log("Message posted to worker");
  };

  second.onchange = function () {
    myWorker.port.postMessage([first.value, second.value]);
    console.log("Message posted to worker");
  };

  myWorker.port.onmessage = function (e) {
    result1.textContent = e.data;
    console.log("Message received from worker");
    console.log(e.lastEventId);
  };
}
}
```

Inside the worker we use the onconnect handler to connect to the same port discussed above. The ports associated with that worker are accessible in the connect event's ports property — we then use MessagePort start() method to start the port, and the onmessage handler to deal with messages sent from the main threads.
while on `worker.js` we have
```js
onconnect = (e) => {
  const port = e.ports[0];

  port.addEventListener('message', (e) => {
    const workerResult = `Result: ${e.data[0] * e.data[1]}`;
    port.postMessage(workerResult);
  });

  port.start(); // Required when using addEventListener. Otherwise called implicitly by onmessage setter.
}
```

if not using `addEventListener` we can have
```js
onconnect = function (event) {
  const port = event.ports[0];

  port.onmessage = function (e) {
    const workerResult = `Result: ${e.data[0] * e.data[1]}`;
    port.postMessage(workerResult);
  };
};
```

---
