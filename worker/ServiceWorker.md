ServiceWorker
===

> Service workers are specialized JavaScript assets that act as proxies between web browsers and web servers. They aim to improve reliability by providing offline access, as well as boost page performance.

- Service workers essentially act as proxy servers that sit between web applications, the browser, and the network (when available). They are intended, among other things, to enable the creation of effective offline experiences, intercept network requests and take appropriate action based on whether the network is available, and update assets residing on the server. They will also allow access to push notifications and background sync APIs.


- A service worker is an event-driven worker registered against an origin and a path. It takes the form of a JavaScript file that can control the web-page/site that it is associated with, intercepting and modifying navigation and resource requests, and caching resources in a very granular fashion to give you complete control over how your app behaves in certain situations (the most obvious one being when the network is not available).

- A service worker is run in a worker context: it therefore has no DOM access, and runs on a different thread to the main JavaScript that powers your app, so it is non-blocking. It is designed to be fully async; as a consequence, APIs such as synchronous XHR and Web Storage can't be used inside a service worker.

- Service workers only run over HTTPS, for security reasons. Most significantly, HTTP connections are susceptible to malicious code injection by man in the middle attacks, and such attacks could be worse if allowed access to these powerful APIs.



## Define `serviceWorker.js` as 
```js
self.addEventListener("install", e => {
    e.waitUntil(
      caches.open("static").then(cache => {
        return cache.addAll(['./','./logo.png','./style.css']);
      })
    );
  });

  self.addEventListener("fetch", e => {
      //console.log(`intercepting fetch Request for: ${e.request.url}`);
    
    e.respondWith(
      caches.match(e.request).then(res => {
        return res || fetch(e.request);
      })
    );
    
  });
 ```
 
 ## Which must be registered in `main.js` as:
 ```js
 if ("serviceWorker" in navigator) {
    //window.addEventListener("load", function() {
      navigator.serviceWorker
        .register("serviceWorker.js")
        .then(res => console.log("service worker registered"))
        .catch(err => console.log("service worker not registered", err))
    //})
  }

 
 ```
