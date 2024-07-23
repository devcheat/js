
**Web Messaging**
===
- [**Web Messaging**](#web-messaging)
  - [Message Event](#message-event)
  - [Attributes](#attributes)
  - [Sending a cross-document message](#sending-a-cross-document-message)
  - [Examples](#examples)
  - [Channel messaging](#channel-messaging)
  - [The MessageChannel and MessagePort Objects](#the-messagechannel-and-messageport-objects)
---




Web messaging is the ability to send realtime messages from the server to the client browser. It overrides the cross domain communication problem in different domains, protocols or ports

For example, you want to send the data from your page to ad container which is placed at iframe or voice-versa, in this scenario, Browser throws a security exception. With web messaging we can pass the data across as a message event.

## Message Event
Message events fires Cross-document messaging, channel messaging, server-sent events and web sockets.it has described by Message Event interface.

## Attributes
Attributes | Description
--|--
data|Contains string data
origin|Contains Domain name and port
lastEventId|Contains unique identifier for the current message event.
source|Contains to A reference to the originating document’s window
ports|Contains the data which is sent by any message port

## Sending a cross-document message
Before send cross document message, we need to create a new web browsing context either by creating new iframe or new window. We can send the data using with postMessage() and it has two arguments. They are as −

- **message** − The message to send
- **targetOrigin** − Origin name

## Examples
Sending message from iframe to button
```js
var iframe = document.querySelector('iframe');
var button = document.querySelector('button');

var clickHandler = function() {
   iframe.contentWindow.postMessage('The message to send.',
      'https://www.tutorialspoint.com);
}
button.addEventListener('click',clickHandler,false);
```

Receiving a cross-document message in the receiving document
```js
var messageEventHandler = function(event){
   
   // check that the origin is one we want.
   if(event.origin == 'https://www.tutorialspoint.com') {
      alert(event.data);
   }
}
window.addEventListener('message', messageEventHandler,false);
```
## Channel messaging
Two-way communication between the browsing contexts is called channel messaging. It is useful for communication across multiple origins.

## The MessageChannel and MessagePort Objects
While creating messageChannel, it internally creates two ports to sending the data and forwarded to another browsing context.

- `postMessage()` − Post the message throw channel

- `start()` − It sends the data

- `close()` − It close the ports

In this scenario, we are sending the data from one iframe to another iframe. Here we are invoking the data in function and passing the data to DOM.
```js
var loadHandler = function() {
   var mc, portMessageHandler;
   mc = new MessageChannel();
   window.parent.postMessage('documentAHasLoaded','http://foo.example',[mc.port2]);
   
   portMessageHandler = function(portMsgEvent) {
      alert( portMsgEvent.data );
   }
   
   mc.port1.addEventListener('message', portMessageHandler, false);
   mc.port1.start();
}
window.addEventListener('DOMContentLoaded', loadHandler, false);
```

Above code, it is taking the data from port 2, now it will pass the data to second iframe
```js
var loadHandler = function() {
   var iframes, messageHandler;
   iframes = window.frames;
   
   messageHandler = function(messageEvent) {
      
      if( messageEvent.ports.length > 0 ) {
         
         // transfer the port to iframe[1]
         iframes[1].postMessage('portopen','http://foo.example',messageEvent.ports);
      }
   }
   window.addEventListener('message',messageHandler,false);
}
window.addEventListener('DOMContentLoaded',loadHandler,false);
```
Now second document handles the data by using the portMsgHandler function.
```js
var loadHandler() {
   
   // Define our message handler function
   var messageHandler = function(messageEvent) {
   
      // Our form submission handler
      
      var formHandler = function() {
         var msg = 'add <foo@example.com> to game circle.';
         messageEvent.ports[0].postMessage(msg);
      }
      document.forms[0].addEventListener('submit',formHandler,false);
   }
   window.addEventListener('message',messageHandler,false);
}
window.addEventListener('DOMContentLoaded',loadHandler,false);
```
---
eof
