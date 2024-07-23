# Web worker
A web worker in JavaScript is a mechanism that enables running scripts in background threads separate from the main execution thread of a web application. This capability allows for multitasking and parallel processing within web applications, which is particularly useful for handling computationally intensive tasks without blocking the user interface (UI).

## 1. Define `web_worker.js` as 

```js
var i=0;

function timedCount() {
    i=i+1;
    postMessage(i);
    setTimeout("timedCount()", 500);
}

timedCount();
```

## 2. Then Call it form page as 
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
