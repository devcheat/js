The Clock WebWorker
===

This is an example of WebWorker
Here is a simple example for WebWorker `clock.js` showing how to communicate between them using `postMessage` & `onmessage`

So we define an  `index.html` page to shoe the result as 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=<device-width>, initial-scale=1.0">
    <title>Document</title>
    <style>
        body{
            color: aliceblue;
            background-color: rgb(16, 16, 16);
        }
        #result {
            font-size: 40px;
            font-weight: bolder;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
    </style>
</head>
<body>
    <div id="result"></div>

    <script>
        if (window.Worker) {
            var ww = new Worker("clock.js"); //initilaize the webworker
            ww.postMessage("[start]"); //command the clock to start
            
            //receive the response and display in the page
            ww.onmessage = function(event) {
                document.getElementById("result").innerHTML = event.data;
            };
        }
    </script>
</body>
</html>
```

and the `clock.js` as 
```js
/*
* clock.js - an example of webworker
*/

//a timer function to post the current date to the caller
function timedCount() {
    var Now = new Date(); //the current datetime updated   
    postMessage(Now); //posting the current date to the invoker
    setTimeout("timedCount()", 500); //recursively call the timerCount() function with a delay of 500 miliseconds
}


// on message receive even handler receiver wahtever is posted from the other side
onmessage = function(e) {
    console.log('Worker: Message received from main script: ' + e.data); //e.data contaisn the parametrs passed to it
    if(e.data == "[start]")
        timedCount();
    else
        postMessage('command not recognizd, please say [start]');
}
```
