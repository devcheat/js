**`OffscreenCanvas`**
===
- [**`OffscreenCanvas`**](#offscreencanvas)
  - [Constructors `OffscreenCanvas()`](#constructors-offscreencanvas)
  - [Instance properties](#instance-properties)
    - [`OffscreenCanvas.height`](#offscreencanvasheight)
    - [`OffscreenCanvas.width`](#offscreencanvaswidth)
  - [Instance methods](#instance-methods)
    - [`OffscreenCanvas.getContext()`](#offscreencanvasgetcontext)
    - [`OffscreenCanvas.convertToBlob()`](#offscreencanvasconverttoblob)
    - [`OffscreenCanvas.transferToImageBitmap()`](#offscreencanvastransfertoimagebitmap)
  - [Synchronous display of frames produced by an `OffscreenCanvas`](#synchronous-display-of-frames-produced-by-an-offscreencanvas)
  - [Asynchronous display of frames produced by an OffscreenCanvas](#asynchronous-display-of-frames-produced-by-an-offscreencanvas)

---
When using the `<canvas>` element or the Canvas API, rendering, animation, and user interaction usually happen on the main execution thread of a web application. The computation relating to canvas animations and rendering can have a significant impact on application performance.

The `OffscreenCanvas` interface provides a canvas that can be rendered off screen, decoupling the DOM and the Canvas API so that the `<canvas>`element is no longer entirely dependent on the DOM. Rendering operations can also be run inside a worker context, allowing you to run some tasks in a separate thread and avoid heavy work on the main thread.

OffscreenCanvas is a transferable object.

**`EventTarget <---- OffscreenCanvas`**

## Constructors `OffscreenCanvas()`
OffscreenCanvas constructor. Creates a new OffscreenCanvas object.

## Instance properties
### `OffscreenCanvas.height`
The height of the offscreen canvas.

### `OffscreenCanvas.width`
The width of the offscreen canvas.

## Instance methods
### `OffscreenCanvas.getContext()`
Returns a rendering context for the offscreen canvas.

### `OffscreenCanvas.convertToBlob()`
Creates a `Blob` object representing the image contained in the canvas.

### `OffscreenCanvas.transferToImageBitmap()`
Creates an `ImageBitmap` object from the most recently rendered image of the OffscreenCanvas.


## Synchronous display of frames produced by an `OffscreenCanvas`
---
One way to use the `OffscreenCanvas` API is to use a rendering context that has been obtained from an `OffscreenCanvas` object to generate new frames. Once a new frame has finished rendering in this context, the `transferToImageBitmap()` method can be called to save the most recent rendered image. This method returns an ImageBitmap object, which can be used in a variety of Web APIs and also in a second canvas without creating a transfer copy.

To display the `ImageBitmap`, you can use a `ImageBitmapRenderingContext` context, which can be created by calling `canvas.getContext("bitmaprenderer")` on a (visible) canvas element. This context only provides functionality to replace the canvas's contents with the given ImageBitmap. A call to `ImageBitmapRenderingContext.transferFromImageBitmap()` with the previously rendered and saved `ImageBitmap` from the `OffscreenCanvas`, will display the `ImageBitmap` on the canvas and transfer its ownership to the canvas. A single `OffscreenCanvas` may transfer frames into an arbitrary number of other `ImageBitmapRenderingContext` objects.

Given these two `<canvas>` elements
```js
<canvas id="one"></canvas> <canvas id="two"></canvas>
```
the following code will provide the rendering using OffscreenCanvas as described above.
```js
const one = document.getElementById("one").getContext("bitmaprenderer");
const two = document.getElementById("two").getContext("bitmaprenderer");

const offscreen = new OffscreenCanvas(256, 256);
const gl = offscreen.getContext("webgl");

// Perform some drawing for the first canvas using the gl context
const bitmapOne = offscreen.transferToImageBitmap();
one.transferFromImageBitmap(bitmapOne);

// Perform some more drawing for the second canvas
const bitmapTwo = offscreen.transferToImageBitmap();
two.transferFromImageBitmap(bitmapTwo);
```

## Asynchronous display of frames produced by an `OffscreenCanvas`
---
Another way to use the OffscreenCanvas API, is to call `transferControlToOffscreen()` on a `<canvas>` element, either on a worker or the main thread, which will return an OffscreenCanvas object from an HTMLCanvasElement object from the main thread. Calling `getContext()` will then obtain a rendering context from that OffscreenCanvas.

**main.js (main thread code):**
```js
//main.js
const htmlCanvas = document.getElementById("canvas");
const offscreen = htmlCanvas.transferControlToOffscreen();

const worker = new Worker("offscreencanvas.js");
worker.postMessage({ canvas: offscreen }, [offscreen]);
```

**offscreencanvas.js (worker code):**
```js
//offscreencanvas.js
onmessage = (evt) => {
  const canvas = evt.data.canvas;
  const gl = canvas.getContext("webgl");

  // Perform some drawing using the gl context
};
```
You can also use requestAnimationFrame in workers
```js
onmessage = (evt) => {
  const canvas = evt.data.canvas;
  const gl = canvas.getContext("webgl");

  function render(time) {
    // Perform some drawing using the gl context
    requestAnimationFrame(render);
  }
  requestAnimationFrame(render);
};
```
---
