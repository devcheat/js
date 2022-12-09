**Web worker**
===
> Web Workers are a simple means for web content to run scripts in background threads. The worker thread can perform tasks without interfering with the user interface.

- In addition, they can perform I/O using XMLHttpRequest (although the responseXML and channel attributes are always null) or fetch (with no such restrictions).

- Once created, a worker can send messages to the JavaScript code that created it by posting messages to an event handler specified by that code (and vice versa).

- A worker is an object created using a constructor (e.g. Worker()) that runs a named JavaScript file — this file contains the code that will run in the worker thread; workers run in another global context that is different from the current window. Thus, using the window shortcut to get the current global scope (instead of self) within a Worker will return an error.

- We can run whatever code you like inside the worker thread, with some exceptions. For example, **you can't directly manipulate the DOM from inside a worker, or use some default methods and properties of the window object**. But you can use a large number of items available under window, including WebSockets, and data storage mechanisms like IndexedDB.

- Data is sent between workers and the main thread via a system of messages --- both sides send their messages using the `postMessage()` method, and respond to messages via the `onmessage` event handler (the message is contained within the [`message`](https://developer.mozilla.org/en-US/docs/Web/API/Worker/message_event "message") event's data attribute). The data is copied rather than shared.

- Workers may, in turn, spawn new workers, as long as those workers are hosted within the same origin as the parent page. In addition, workers may use [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) for network I/O, with the exception that the `responseXML` and `channel` attributes on `XMLHttpRequest` always return `null`.


## Example Code 
Define `web_worker.js` as 

```js
var i=0;

function timedCount() {
    i=i+1;
    postMessage(i);
    setTimeout("timedCount()", 500);
}

timedCount();
```

then Call it form page script as 
```js
if (window.Worker) {
  var ww = new Worker("web_workers.js");

   ww.onmessage = function(event) {
      document.getElementById("result").innerHTML = event.data;
    };

}
```
and to destroy it
```js
ww.terminate();
ww = undefined;

```


This can be modified as 
```js
var w;

function startWorker() {
  if(typeof(Worker) !== "undefined") {
    if(typeof(w) == "undefined") {
      w = new Worker("web_workers.js");
    }
    w.onmessage = function(event) {
      document.getElementById("result").innerHTML = event.data;
    };
  } else {
    document.getElementById("result").innerHTML = "Sorry, your browser does not support Web Workers...";
  }
}

function stopWorker() { 
  w.terminate();
  w = undefined;
}
```

A webworker can also receive a message through `onmessage` and can respond to it. For a WebWorker it must be defiend as
```js

onmessage = function(e) {
    console.log('Worker: Message received from main script: ' + e.data);
    timedCount();
}
```






---
