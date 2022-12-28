**`XMLHttpRequest` (XHR)**
===

- [**`XMLHttpRequest` (XHR)**](#xmlhttprequest-xhr)
  - [Constructor `XMLHttpRequest()`](#constructor-xmlhttprequest)
  - [Instance properties](#instance-properties)
    - [`XMLHttpRequest.readyState` Read only](#xmlhttprequestreadystate-read-only)
    - [`XMLHttpRequest.response` Read only](#xmlhttprequestresponse-read-only)
    - [`XMLHttpRequest.responseText` Read only](#xmlhttprequestresponsetext-read-only)
    - [`XMLHttpRequest.responseType`](#xmlhttprequestresponsetype)
    - [`XMLHttpRequest.responseURL` Read only](#xmlhttprequestresponseurl-read-only)
    - [`XMLHttpRequest.responseXML` Read only](#xmlhttprequestresponsexml-read-only)
    - [`XMLHttpRequest.status` Read only](#xmlhttprequeststatus-read-only)
    - [`XMLHttpRequest.statusText` Read only](#xmlhttprequeststatustext-read-only)
    - [`XMLHttpRequest.timeout`](#xmlhttprequesttimeout)
    - [`XMLHttpRequest.upload` Read only](#xmlhttprequestupload-read-only)
    - [`XMLHttpRequest.withCredentials`](#xmlhttprequestwithcredentials)
  - [Non-standard properties](#non-standard-properties)
    - [`XMLHttpRequest.channel` Read only](#xmlhttprequestchannel-read-only)
    - [`XMLHttpRequest.mozAnon` Read only](#xmlhttprequestmozanon-read-only)
    - [`XMLHttpRequest.mozSystem` Read only](#xmlhttprequestmozsystem-read-only)
    - [`XMLHttpRequest.mozBackgroundRequest`](#xmlhttprequestmozbackgroundrequest)
  - [Instance methods](#instance-methods)
    - [`XMLHttpRequest.abort()`](#xmlhttprequestabort)
    - [`XMLHttpRequest.getAllResponseHeaders()`](#xmlhttprequestgetallresponseheaders)
    - [`XMLHttpRequest.getResponseHeader()`](#xmlhttprequestgetresponseheader)
    - [`XMLHttpRequest.open()`](#xmlhttprequestopen)
    - [`XMLHttpRequest.overrideMimeType()`](#xmlhttprequestoverridemimetype)
    - [`XMLHttpRequest.send()`](#xmlhttprequestsend)
    - [`XMLHttpRequest.setRequestHeader()`](#xmlhttprequestsetrequestheader)
  - [Events](#events)
    - [`abort`](#abort)
    - [`error`](#error)
    - [`load`](#load)
    - [`loadend`](#loadend)
    - [`loadstart`](#loadstart)
    - [`progress`](#progress)
    - [`readystatechange`](#readystatechange)
    - [`timeout`](#timeout)
  - [Using `XMLHttpRequest`](#using-xmlhttprequest)
    - [Types of requests](#types-of-requests)
    - [Handling responses](#handling-responses)
      - [Analyzing and manipulating the responseXML property](#analyzing-and-manipulating-the-responsexml-property)
      - [Processing a responseText property containing an HTML document](#processing-a-responsetext-property-containing-an-html-document)
  - [Handling binary data](#handling-binary-data)
  - [Monitoring progress](#monitoring-progress)
    - [`progress`](#progress-1)
    - [`load`](#load-1)
  - [Submitting forms and uploading files](#submitting-forms-and-uploading-files)
    - [Using nothing but `XMLHttpRequest`](#using-nothing-but-xmlhttprequest)
      - [A brief introduction to the submit methods](#a-brief-introduction-to-the-submit-methods)
      - [A little vanilla framework](#a-little-vanilla-framework)
      - [Using FormData objects](#using-formdata-objects)
  - [Get last modified date](#get-last-modified-date)
  - [Cross-site `XMLHttpRequest`](#cross-site-xmlhttprequest)
    - [Bypassing the cache](#bypassing-the-cache)
  - [Security](#security)
    - [XMLHttpRequests being stopped](#xmlhttprequests-being-stopped)

---
`XMLHttpRequest` (XHR) objects are used to interact with servers. You can retrieve data from a URL without having to do a full page refresh. This enables a Web page to update just part of a page without disrupting what the user is doing.


Despite its name, XMLHttpRequest can be used to retrieve any type of data, not just XML.

## Constructor `XMLHttpRequest()`
The constructor initializes an XMLHttpRequest. It must be called before any other method calls.

## Instance properties
This interface also inherits properties of XMLHttpRequestEventTarget and of EventTarget.

### `XMLHttpRequest.readyState` Read only
Returns a number representing the state of the request.

### `XMLHttpRequest.response` Read only
Returns an ArrayBuffer, a Blob, a Document, a JavaScript object, or a string, depending on the value of XMLHttpRequest.responseType, that contains the response entity body.

### `XMLHttpRequest.responseText` Read only
Returns a string that contains the response to the request as text, or null if the request was unsuccessful or has not yet been sent.

### `XMLHttpRequest.responseType`
Specifies the type of the response.

### `XMLHttpRequest.responseURL` Read only
Returns the serialized URL of the response or the empty string if the URL is null.

### `XMLHttpRequest.responseXML` Read only
Returns a Document containing the response to the request, or null if the request was unsuccessful, has not yet been sent, or cannot be parsed as XML or HTML. Not available in Web Workers.

### `XMLHttpRequest.status` Read only
Returns the HTTP response status code of the request.

### `XMLHttpRequest.statusText` Read only
Returns a string containing the response string returned by the HTTP server. Unlike XMLHttpRequest.status, this includes the entire text of the response message ("OK", for example).

> **Note:** According to the HTTP/2 specification RFC 7540, section 8.1.2.4: Response Pseudo-Header Fields, HTTP/2 does not define a way to carry the version or reason phrase that is included in an HTTP/1.1 status line.

### `XMLHttpRequest.timeout`
The time in milliseconds a request can take before automatically being terminated.

### `XMLHttpRequest.upload` Read only
A XMLHttpRequestUpload representing the upload process.

### `XMLHttpRequest.withCredentials`
Returns true if cross-site Access-Control requests should be made using credentials such as cookies or authorization headers; otherwise 

## Non-standard properties
### `XMLHttpRequest.channel` Read only
The channel used by the object when performing the request.

### `XMLHttpRequest.mozAnon` Read only
A boolean. If true, the request will be sent without cookie and authentication headers.

### `XMLHttpRequest.mozSystem` Read only
A boolean. If true, the same origin policy will not be enforced on the request.

### `XMLHttpRequest.mozBackgroundRequest`
A boolean. It indicates whether or not the object represents a background service request.

## Instance methods
### `XMLHttpRequest.abort()`
Aborts the request if it has already been sent.

### `XMLHttpRequest.getAllResponseHeaders()`
Returns all the response headers, separated by CRLF, as a string, or null if no response has been received.

### `XMLHttpRequest.getResponseHeader()`
Returns the string containing the text of the specified header, or null if either the response has not yet been received or the header doesn't exist in the response.

### `XMLHttpRequest.open()`
Initializes a request.

### `XMLHttpRequest.overrideMimeType()`
Overrides the MIME type returned by the server.

### `XMLHttpRequest.send()`
Sends the request. If the request is asynchronous (which is the default), this method returns as soon as the request is sent.

### `XMLHttpRequest.setRequestHeader()`
Sets the value of an HTTP request header. You must call setRequestHeader() after open(), but before send().

## Events
### `abort`
Fired when a request has been aborted, for example because the program called XMLHttpRequest.abort(). Also available via the onabort event handler property.

### `error`
Fired when the request encountered an error. Also available via the onerror event handler property.

### `load`
Fired when an XMLHttpRequest transaction completes successfully. Also available via the onload event handler property.

### `loadend`
Fired when a request has completed, whether successfully (after load) or unsuccessfully (after abort or error). Also available via the onloadend event handler property.

### `loadstart`
Fired when a request has started to load data. Also available via the onloadstart event handler property.

### `progress`
Fired periodically when a request receives more data. Also available via the onprogress event handler property.

### `readystatechange`
Fired whenever the readyState property changes. Also available via the onreadystatechange event handler property.

### `timeout`
Fired when progress is terminated due to preset time expiring. Also available via the ontimeout event handler property.


## Using `XMLHttpRequest`
In this guide, we'll take a look at how to use `XMLHttpRequest` to issue HTTP requests in order to exchange data between the web site and a server.

Examples of both common and more obscure use cases for ``XMLHttpRequest`` are included.

To send an HTTP request, create an `XMLHttpRequest` object, open a URL, and send the request. After the transaction completes, the object will contain useful information such as the response body and the HTTP status of the result.
```js
function reqListener() {
  console.log(this.responseText);
}

const req = new XMLHttpRequest();
req.addEventListener("load", reqListener);
req.open("GET", "http://www.example.org/example.txt");
req.send();
```
### Types of requests
A request made via `XMLHttpRequest` can fetch the data in one of two ways, asynchronously or synchronously. The type of request is dictated by the optional async argument (the third argument) that is set on the `XMLHttpRequest`.open() method. 

If this argument is true or not specified, the ``XMLHttpRequest`` is processed asynchronously, otherwise the process is handled synchronously. A detailed discussion and demonstrations of these two types of requests can be found on the synchronous and asynchronous requests page. You can't use synchronous requests outside web workers as it freezes the main interface.

> **Note:** The constructor `XMLHttpRequest` isn't limited to only XML documents. It starts with "XML" because when it was created the main format that was originally used for asynchronous data exchange was XML.

### Handling responses
There are several types of response attributes defined for the `XMLHttpRequest()` constructor. These tell the client making the `XMLHttpRequest` important information about the status of the response. Some cases where dealing with non-text response types may involve some manipulation and analysis are outlined in the following sections.

#### Analyzing and manipulating the responseXML property

If you use `XMLHttpRequest` to get the content of a remote XML document, the responseXML property will be a DOM object containing a parsed XML document. This could prove difficult to manipulate and analyze. There are four primary ways of analyzing this XML document:

- Using XPath to address (or point to) parts of it.
- Manually Parsing and serializing XML to strings or objects.
- Using XMLSerializer to serialize DOM trees to strings or to files.
- RegExp can be used if you always know the content of the XML document beforehand. You might want to remove line breaks, if you use RegExp to scan with regard to line breaks. However, this method is a "last resort" since if the XML code changes slightly, the method will likely fail.
> **Note:** `XMLHttpRequest` can now interpret HTML for you using the responseXML property. Read the article about HTML in `XMLHttpRequest` to learn how to do this.

#### Processing a responseText property containing an HTML document
If you use `XMLHttpRequest` to get the content of a remote HTML webpage, the responseText property is a string containing the raw HTML. This could prove difficult to manipulate and analyze. There are three primary ways to analyze and parse this raw HTML string:

- Use the `XMLHttpRequest.responseXML` property as covered in the article HTML in `XMLHttpRequest`.
- Inject the content into the body of a document fragment via fragment.body.innerHTML and traverse the DOM of the fragment.
- RegExp can be used if you always know the content of the HTML responseText beforehand. You might want to remove line breaks, if you use RegExp to scan with regard to line breaks. However, this method is a "last resort" since if the HTML code changes slightly, the method will likely fail.

## Handling binary data
Although `XMLHttpRequest` is most commonly used to send and receive textual data, it can be used to send and receive binary content. There are several well tested methods for coercing the response of an `XMLHttpRequest` into sending binary data. These involve utilizing the overrideMimeType() method on the `XMLHttpRequest` object and is a workable solution.
```js
const req = new XMLHttpRequest();
req.open("GET", url);
// retrieve data unprocessed as a binary string
req.overrideMimeType("text/plain; charset=x-user-defined");
/* ... */
```
However, more modern techniques are available, since the responseType attribute now supports a number of additional content types, which makes sending and receiving binary data much easier.

For example, consider this snippet, which uses the responseType of "arraybuffer" to fetch the remote content into a ArrayBuffer object, which stores the raw binary data.
```js
const req = new XMLHttpRequest();

req.onload = (e) => {
  const arraybuffer = req.response; // not responseText
  /* ... */
};
req.open("GET", url);
req.responseType = "arraybuffer";
req.send();
```
For more examples check out the Sending and Receiving Binary Data page.

## Monitoring progress
`XMLHttpRequest` provides the ability to listen to various events that can occur while the request is being processed. This includes periodic progress notifications, error notifications, and so forth.

Support for DOM progress event monitoring of `XMLHttpRequest` transfers follows the specification for progress events: these events implement the ProgressEvent interface. The actual events you can monitor to determine the state of an ongoing transfer are:

### `progress`
The amount of data that has been retrieved has changed.

### `load`
The transfer is complete; all data is now in the response
```js
const req = new XMLHttpRequest();

req.addEventListener("progress", updateProgress);
req.addEventListener("load", transferComplete);
req.addEventListener("error", transferFailed);
req.addEventListener("abort", transferCanceled);

req.open();

// ...

// progress on transfers from the server to the client (downloads)
function updateProgress(event) {
  if (event.lengthComputable) {
    const percentComplete = (event.loaded / event.total) * 100;
    // ...
  } else {
    // Unable to compute progress information since the total size is unknown
  }
}

function transferComplete(evt) {
  console.log("The transfer is complete.");
}

function transferFailed(evt) {
  console.log("An error occurred while transferring the file.");
}

function transferCanceled(evt) {
  console.log("The transfer has been canceled by the user.");
}
```

Lines 3-6 add event listeners for the various events that are sent while performing a data transfer using `XMLHttpRequest`.

> **Note:** You need to add the event listeners before calling open() on the request. Otherwise the progress events will not fire.

The progress event handler, specified by the updateProgress() function in this example, receives the total number of bytes to transfer as well as the number of bytes transferred so far in the event's total and loaded fields. However, if the lengthComputable field is false, the total length is not known and will be zero.

Progress events exist for both download and upload transfers. The download events are fired on the `XMLHttpRequest` object itself, as shown in the above sample. The upload events are fired on the `XMLHttpRequest`.upload object, as shown below:
```js
const req = new XMLHttpRequest();

req.upload.addEventListener("progress", updateProgress);
req.upload.addEventListener("load", transferComplete);
req.upload.addEventListener("error", transferFailed);
req.upload.addEventListener("abort", transferCanceled);

oReq.open();
```
> **Note:** Progress events are not available for the file: protocol.

Progress events come in for every chunk of data received, including the last chunk in cases in which the last packet is received and the connection closed before the progress event is fired. In this case, the progress event is automatically fired when the load event occurs for that packet. This lets you now reliably monitor progress by only watching the "progress" event.

One can also detect all three load-ending conditions (abort, load, or error) using the loadend event:
```js
req.addEventListener("loadend", loadEnd);

function loadEnd(e) {
  console.log(
    "The transfer finished (although we don't know if it succeeded or not)."
  );
}
```
> Note there is no way to be certain, from the information received by the loadend event, as to which condition caused the operation to terminate; however, you can use this to handle tasks that need to be performed in all end-of-transfer scenarios.

## Submitting forms and uploading files
Instances of `XMLHttpRequest` can be used to submit forms in two ways:

- standalone, without any API,
- using the FormData API.

Using the FormData API is the simplest and fastest, but has the disadvantage that data collected can not be stringified. Using only XHR is more complex, but typically more flexible and powerful.

### Using nothing but `XMLHttpRequest`
Submitting forms without the FormData API does not require other APIs for most use cases. The only case where you need an additional API is if you want to upload one or more files, where you use the FileReader API.

#### A brief introduction to the submit methods
An HTML <form> can be sent in four ways:

- using the POST method and setting the enctype attribute to application/x-www-form-urlencoded (default);
- using the POST method and setting the enctype attribute to text/plain;
- using the POST method and setting the enctype attribute to multipart/form-data;
- using the GET method (in this case the enctype attribute will be ignored).

Now, consider the submission of a form containing only two fields, named foo and baz. If you are using the POST method the server will receive a string similar to one of the following three examples, depending on the encoding type you are using:

- Method: `POST`; Encoding type: `application/x-www-form-urlencoded` (default):
```js
Content-Type: application/x-www-form-urlencoded

foo=bar&baz=The+first+line.%0D%0AThe+second+line.%0D%0A
```

- Method: `POST`; Encoding type: `text/plain`:
```js
Content-Type: text/plain

foo=bar
baz=The first line.
The second line.
```

- Method: `POST`; Encoding type: `multipart/form-data`:
```JS
Content-Type: multipart/form-data; boundary=---------------------------314911788813839

-----------------------------314911788813839
Content-Disposition: form-data; name="foo"

bar
-----------------------------314911788813839
Content-Disposition: form-data; name="baz"

The first line.
The second line.

-----------------------------314911788813839--
```
However, if you are using the GET method, a string like the following will be added to the URL:
```JS
?foo=bar&baz=The%20first%20line.%0AThe%20second%20line.
```
#### A little vanilla framework
All these effects are done automatically by the web browser whenever you submit a <form>. If you want to perform the same effects using JavaScript you have to instruct the interpreter about everything. Therefore, how to send forms in pure XHR is too complex to be explained here in detail. For this reason, here we place a complete (yet didactic) framework, able to use all four ways to submit, and to upload files:
```HTML
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Sending forms with pure AJAX &ndash; MDN</title>
    <script>
      "use strict";

      // :: XHR Form Submit Framework ::
      //
      // https://developer.mozilla.org/en-US/docs/DOM/XMLHttpRequest/Using_XMLHttpRequest
      //
      // This framework is released under the GNU Public License, version 3 or later.
      // https://www.gnu.org/licenses/gpl-3.0-standalone.html
      //
      // Syntax:
      //
      // XHRSubmit(HTMLFormElement);
      const XHRSubmit = (function () {
        function xhrSuccess() {
          console.log(this.responseText);
          // you can get the serialized data through the "submittedData" custom property:
          // console.log(JSON.stringify(this.submittedData));
        }

        function submitData(data) {
          const req = new XMLHttpRequest();
          req.submittedData = data;
          req.onload = xhrSuccess;
          if (data.technique === 0) {
            // method is GET
            req.open(
              "get",
              data.receiver.replace(
                /(?:\?.*)?$/,
                data.segments.length > 0 ? `?${data.segments.join("&")}` : ""
              ),
              true
            );
            req.send(null);
          } else {
            // method is POST
            req.open("post", data.receiver, true);
            if (data.technique === 3) {
              // enctype is multipart/form-data
              const boundary =
                "---------------------------" + Date.now().toString(16);
              req.setRequestHeader(
                "Content-Type",
                `multipart\/form-data; boundary=${boundary}`
              );
              req.sendAsBinary(
                `--${boundary}\r\n` +
                  data.segments.join(`--${boundary}\r\n`) +
                  `--${boundary}--\r\n`
              );
            } else {
              // enctype is application/x-www-form-urlencoded or text/plain
              req.setRequestHeader("Content-Type", data.contentType);
              req.send(data.segments.join(data.technique === 2 ? "\r\n" : "&"));
            }
          }
        }

        function processStatus(data) {
          if (data.status > 0) {
            return;
          }
          // the form is now totally serialized! do something before sending it to the server…
          // doSomething(data);
          // console.log("XHRSubmit - The form is now serialized. Submitting...");
          submitData(data);
        }

        function pushSegment(segment) {
          this.owner.segments[this.segmentIdx] +=
            segment.target.result + "\r\n";
          this.owner.status--;
          processStatus(this.owner);
        }

        function plainEscape(text) {
          // How should I treat a text/plain form encoding?
          // What characters are not allowed? this is what I suppose…:
          // "4\3\7 - Einstein said E=mc2" ----> "4\\3\\7\ -\ Einstein\ said\ E\=mc2"
          return text.replace(/[\s\=\\]/g, "\\$&");
        }

        function SubmitRequest(target) {
          const isPost = target.method.toLowerCase() === "post";
          this.contentType =
            isPost && target.enctype
              ? target.enctype
              : "application\/x-www-form-urlencoded";
          this.technique = isPost
            ? this.contentType === "multipart\/form-data"
              ? 3
              : this.contentType === "text\/plain"
              ? 2
              : 1
            : 0;
          this.receiver = target.action;
          this.status = 0;
          this.segments = [];
          const filter = this.technique === 2 ? plainEscape : escape;
          for (const field of target.elements) {
            if (!field.hasAttribute("name")) {
              continue;
            }
            const fieldType =
              field.nodeName.toUpperCase() === "INPUT" &&
              field.hasAttribute("type")
                ? field.getAttribute("type").toUpperCase()
                : "TEXT";
            if (fieldType === "FILE" && field.files.length > 0) {
              if (this.technique === 3) {
                // enctype is multipart/form-data
                for (const file of field.files) {
                  const segmReq = new FileReader();

                  // Custom properties:
                  segmReq.segmentIdx = this.segments.length;
                  segmReq.owner = this;

                  segmReq.onload = pushSegment;
                  this.segments.push(
                    'Content-Disposition: form-data; name="' +
                      field.name +
                      '"; filename="' +
                      file.name +
                      '"\r\nContent-Type: ' +
                      file.type +
                      "\r\n\r\n"
                  );
                  this.status++;
                  segmReq.readAsBinaryString(file);
                }
              } else {
                // enctype is application/x-www-form-urlencoded or text/plain or
                // method is GET: files will not be sent!
                for (const file of field.files) {
                  this.segments.push(
                    `${filter(field.name)}=${filter(file.name)}`
                  );
                }
              }
            } else if (
              (fieldType !== "RADIO" && fieldType !== "CHECKBOX") ||
              field.checked
            ) {
              // NOTE: this will submit _all_ submit buttons. Detecting the correct one is non-trivial.
              // field type is not FILE or is FILE but is empty.
              if (this.technique === 3) {
                // enctype is multipart/form-data
                this.segments.push(
                  `Content-Disposition: form-data; name="${field.name}"\r\n\r\n${field.value}\r\n`
                );
              } else {
                // enctype is application/x-www-form-urlencoded or text/plain or method is GET
                this.segments.push(
                  `${filter(field.name)}=${filter(field.value)}`
                );
              }
            }
          }
          processStatus(this);
        }

        return (formElement) => {
          if (!formeElement.action) {
            return;
          }
          new SubmitRequest(formElement);
        };
      })();
    </script>
  </head>
  <body>
    <h1>Sending forms with XHR</h1>

    <h2>Using the GET method</h2>

    <form
      action="register.php"
      method="get"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Registration example</legend>
        <p>
          <label>First name: <input type="text" name="firstname" /></label><br />
          <label>Last name: <input type="text" name="lastname" /></label>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>

    <h2>Using the POST method</h2>
    <h3>Enctype: application/x-www-form-urlencoded (default)</h3>

    <form
      action="register.php"
      method="post"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Registration example</legend>
        <p>
          <label>First name:
            <input type="text" name="firstname" />
          </label><br />
          <label>Last name:
            <input type="text" name="lastname" />
          </label>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>

    <h3>Enctype: text/plain</h3>

    <form
      action="register.php"
      method="post"
      enctype="text/plain"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Registration example</legend>
        <p>
          <label>Your name:
            <input type="text" name="user" />
          </label>
        </p>
        <p>
          <label>Your message:<br />
            <textarea name="message" cols="40" rows="8"></textarea>
          </label>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>

    <h3>Enctype: multipart/form-data</h3>

    <form
      action="register.php"
      method="post"
      enctype="multipart/form-data"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Upload example</legend>
        <p>
          <label>First name: <input type="text" name="firstname" /></label><br />
          <label>Last name: <input type="text" name="lastname" /></label><br />
          Sex:
          <input id="sex_male" type="radio" name="sex" value="male" />
          <label for="sex_male">Male</label>
          <input id="sex_female" type="radio" name="sex" value="female" />
          <label for="sex_female">Female</label><br />
          Password: <input type="password" name="secret" /><br />
          <label>What do you prefer:
            <select name="image_type">
              <option>Books</option>
              <option>Cinema</option>
              <option>TV</option>
            </select>
          </label>
        </p>
        <p>
          <label>Post your photos:
            <input type="file" multiple name="photos[]" />
          </label>
        </p>
        <p>
          <input
            id="vehicle_bike"
            type="checkbox"
            name="vehicle[]"
            value="Bike" />
          <label for="vehicle_bike">I have a bike</label><br />
          <input
            id="vehicle_car"
            type="checkbox"
            name="vehicle[]"
            value="Car" />
          <label for="vehicle_car">I have a car</label>
        </p>
        <p>
          <label>Describe yourself:<br />
            <textarea name="description" cols="50" rows="8"></textarea>
          </label>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>
  </body>
</html>
```
To test this, create a page named register.php (which is the action attribute of these sample forms), and put the following minimalistic content:
```php
<?php
  /* register.php */

  header("Content-type: text/plain");

  /*
  NOTE: You should never use `print_r()` in production scripts, or
  otherwise output client-submitted data without sanitizing it first.
  Failing to sanitize can lead to cross-site scripting vulnerabilities.
  */

  echo ":: data received via GET ::\n\n";
  print_r($_GET);

  echo "\n\n:: Data received via POST ::\n\n";
  print_r($_POST);

  echo "\n\n:: Data received as \"raw\" (text/plain encoding) ::\n\n";
  if (isset($HTTP_RAW_POST_DATA)) { echo $HTTP_RAW_POST_DATA; }

  echo "\n\n:: Files received ::\n\n";
  print_r($_FILES);
>
```
The syntax to activate this script is:
```js
XHRSubmit(myForm);
```
> Note: This framework uses the FileReader API to transmit file uploads. This is a recent API and is not implemented in IE9 or below. For this reason, the AJAX-only upload is considered an experimental technique. If you do not need to upload binary files, this framework works fine in most browsers.

> Note: The best way to send binary content is via ArrayBuffers or Blobs in conjunction with the send() method and possibly the readAsArrayBuffer() method of the FileReader API. But, since the aim of this script is to work with a stringifiable raw data, we used the sendAsBinary() method in conjunction with the readAsBinaryString() method of the FileReader API. As such, the above script makes sense only when you are dealing with small files. If you do not intend to upload binary content, consider instead using the FormData API.

#### Using FormData objects
The FormData constructor lets you compile a set of key/value pairs to send using `XMLHttpRequest`. Its primary use is in sending form data, but can also be used independently from a form in order to transmit user keyed data. The transmitted data is in the same format the form's submit() method uses to send data, if the form's encoding type were set to "multipart/form-data". FormData objects can be utilized in a number of ways with an `XMLHttpRequest`. For examples, and explanations of how one can utilize FormData with XMLHttpRequests, see the Using FormData Objects page. For didactic purposes here is a translation of the previous example transformed to use the FormData API. Note the brevity of the code:
```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Sending forms with FormData &ndash; MDN</title>
    <script>
      "use strict";

      function xhrSuccess () {
        console.log(this.responseText);
      }

      function XHRSubmit (formElement) {
        if (!formElement.action) { return; }
        const req = new XMLHttpRequest();
        req.onload = xhrSuccess;
        if (fFormElement.method.toLowerCase() === "post") {
          req.open("post", formElement.action);
          req.send(new FormData(formElement));
        } else {
          let search = "";
          for (const field of formElement.elements) {
            if (!field.hasAttribute("name")) { continue; }
            const fieldType = field.nodeName.toUpperCase() === "INPUT" && oField.hasAttribute("type")
              ? field.getAttribute("type").toUpperCase()
              : "TEXT";
            if (fieldType === "FILE") {
              for (const file of field.files) {
                search += `&${escape(field.name)}=${escape(file.name)}`;
            } else if ((fieldType !== "RADIO" && fieldType !== "CHECKBOX") || field.checked) {
              search += `&${escape(field.name)}=${escape(field.value)}`;
            }
          }
          req.open("get", formElement.action.replace(/(?:\?.*)?$/, search.replace(/^&/, "?")), true);
          req.send(null);
        }
      }
    </script>
  </head>
  <body>
    <h1>Sending forms with FormData</h1>

    <h2>Using the GET method</h2>

    <form
      action="register.php"
      method="get"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Registration example</legend>
        <p>
          First name: <input type="text" name="firstname" /><br />
          Last name: <input type="text" name="lastname" />
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>

    <h2>Using the POST method</h2>
    <h3>Enctype: application/x-www-form-urlencoded (default)</h3>

    <form
      action="register.php"
      method="post"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Registration example</legend>
        <p>
          First name: <input type="text" name="firstname" /><br />
          Last name: <input type="text" name="lastname" />
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>

    <h3>Enctype: text/plain</h3>

    <p>The text/plain encoding is not supported by the FormData API.</p>

    <h3>Enctype: multipart/form-data</h3>

    <form
      action="register.php"
      method="post"
      enctype="multipart/form-data"
      onsubmit="AJAXSubmit(this); return false;">
      <fieldset>
        <legend>Upload example</legend>
        <p>
          First name: <input type="text" name="firstname" /><br />
          Last name: <input type="text" name="lastname" /><br />
          Sex:
          <input id="sex_male" type="radio" name="sex" value="male" />
          <label for="sex_male">Male</label>
          <input id="sex_female" type="radio" name="sex" value="female" />
          <label for="sex_female">Female</label><br />
          Password: <input type="password" name="secret" /><br />
          What do you prefer:
          <select name="image_type">
            <option>Books</option>
            <option>Cinema</option>
            <option>TV</option>
          </select>
        </p>
        <p>
          Post your photos:
          <input type="file" multiple name="photos[]" />
        </p>
        <p>
          <input
            id="vehicle_bike"
            type="checkbox"
            name="vehicle[]"
            value="Bike" />
          <label for="vehicle_bike">I have a bike</label><br />
          <input
            id="vehicle_car"
            type="checkbox"
            name="vehicle[]"
            value="Car" />
          <label for="vehicle_car">I have a car</label>
        </p>
        <p>
          Describe yourself:<br />
          <textarea name="description" cols="50" rows="8"></textarea>
        </p>
        <p>
          <input type="submit" value="Submit" />
        </p>
      </fieldset>
    </form>
  </body>
</html>
```
> Note: As we said, FormData objects are not stringifiable objects. If you want to stringify a submitted data, use the previous pure-AJAX example. Note also that, although in this example there are some file `<input>` fields, when you submit a form through the FormData API you do not need to use the FileReader API also: files are automatically loaded and uploaded.


## Get last modified date
```js
function getHeaderTime() {
  console.log(this.getResponseHeader("Last-Modified")); // A valid GMTString date or null
}

const req = new XMLHttpRequest();
req.open(
  "HEAD", // use HEAD when you only need the headers
  "yourpage.html"
);
req.onload = getHeaderTime;
req.send();
```
Do something when last modified date changes
Let's create two functions:
```js
function getHeaderTime() {
  const lastVisit = parseFloat(
    window.localStorage.getItem(`lm_${this.filepath}`)
  );
  const lastModified = Date.parse(this.getResponseHeader("Last-Modified"));

  if (isNaN(lastVisit) || lastModified > lastVisit) {
    window.localStorage.setItem(`lm_${this.filepath}`, Date.now());
    isFinite(lastVisit) && this.callback(lastModified, lastVisit);
  }
}

function ifHasChanged(URL, callback) {
  const req = new XMLHttpRequest();
  req.open("HEAD" /* use HEAD - we only need the headers! */, URL);
  req.callback = callback;
  req.filepath = URL;
  req.onload = getHeaderTime;
  req.send();
}
```
And to test:
```js
// Let's test the file "yourpage.html"
ifHasChanged("yourpage.html", function (modified, visit) {
  console.log(
    `The page '${this.filepath}' has been changed on ${new Date(
      nModified
    ).toLocaleString()}!`
  );
});
```
If you want to know if the current page has changed, refer to the article about document.lastModified.

## Cross-site `XMLHttpRequest`
Modern browsers support cross-site requests by implementing the Cross-Origin Resource Sharing (CORS) standard. As long as the server is configured to allow requests from your web application's origin, XMLHttpRequest will work. Otherwise, an INVALID_ACCESS_ERR exception is thrown.

### Bypassing the cache
A cross-browser compatible approach to bypassing the cache is appending a timestamp to the URL, being sure to include a "?" or "&" as appropriate. For example:
```
http://foo.com/bar.html -> http://foo.com/bar.html?12345
http://foo.com/bar.html?foobar=baz -> http://foo.com/bar.html?foobar=baz&12345
```
As the local cache is indexed by URL, this causes every request to be unique, thereby bypassing the cache.

You can automatically adjust URLs using the following code:
```js
const req = new XMLHttpRequest();

req.open("GET", url + (/\?/.test(url) ? "&" : "?") + new Date().getTime());
req.send(null);
```

## Security
The recommended way to enable cross-site scripting is to use the Access-Control-Allow-Origin HTTP header in the response to the `XMLHttpRequest`.

### XMLHttpRequests being stopped
If you conclude with an `XMLHttpRequest` receiving status=0 and statusText=null, this means the request was not allowed to be performed. It was UNSENT. A likely cause for this is when the `XMLHttpRequest` origin (at the creation of the `XMLHttpRequest`) has changed when the `XMLHttpRequest` is subsequently `open()`. 

This case can happen, for example, when one has an `XMLHttpRequest` that gets fired on an onunload event for a window, the expected `XMLHttpRequest` is created when the window to be closed is still there, and finally sending the request (in other words, `open()`) when this window has lost its focus and another window gains focus. The most effective way to avoid this problem is to set a listener on the new window's DOMActivate event which is set once the terminated window has its unload event triggered.

---
