# Required Browser Features

The page describes the features that are required for a web browser to have to PDF.js function properly. Some of the features are critical and does not let PDF.js function properly if they are not supported or disabled. Some of them can be emulated if absent, however the PDF.js performance and memory usage will be worse than when the feature if present.

## <a id="canvas"></a>CANVAS element is present

Support of the CANVAS element and "2d" context is required feature for PDF.js.
No emulation of the CANVAS element is provided in browsers that do not support it.


## <a id="get-literal"></a>get-literal properties

The core library defines object properties using object 'get' literal:

```
var obj = {
  get prop() { return 1; }
};
```

Browsers that don't understand this syntax will not be able to execute the code.


## <a id="addEventListener"></a>addEventListener is present

The `addEventListener` method is used to bind event listeners for DOM elements.
No emulation of the `addEventListener` method is provided in browsers that do not support it.


## <a id="Uint8Array"></a><a id="Uint16Array"></a><a id="Int32Array"></a><a id="Float32Array"></a><a id="Float64Array"></a>Typed arrays are present

The `Uint8Array`, `Uint16Array`, `Int32Array`, `Float32Array` and `Float64Array` will be replaced
by the artificial TypedArray object if those types are not implemented natively.

The emulated typed arrays are slower, don't truncate the items to specific data types and they are memory inefficient. Only `subarray`, `buffer`, `set` and `byteLength` are similated. The `subarray` just clones the array. The `set` method is provided to emulate the `Uint8Array` the method.

If the `Float32Array` native implementation exists and the `Float64Array` is absent, then the `Float32Array` will be used instead of `Float64Array`.

## <a id="Object-create"></a>Object.create() is present

The `Object.create` method will be added to the `Object` function if native implementation is absent.


## <a id="Object-defineProperty"></a>Object.defineProperty() is present


The `Object.defineProperty` method will be added to the `Object` function if native implementation is absent. The `__defineGetter__` / `__defineSetter__` will be used instead.


## <a id="Object-defineProperty-DOM"></a>Object.defineProperty() can be used with DOM objects

Some browsers do not allow using the `Object.defineProperty` with DOM objects.
In this case, the `Object.defineProperty` be replaced by the artificial one. See [Object.defineProperty() is present](#Object-defineProperty).


## <a id="get-literal-redefine"></a>Defined via get-literal properties can be redefined

Some browsers does not allow redefine properties defined with get literal by the `Object.defineProperty`.
In this case, the `Object.defineProperty` be replaced by the artificial one. See [Object.defineProperty() is present](#Object-defineProperty).


## <a id="Object-keys"></a>Object.keys() is present

The `Object.keys` method will be added to the `Object` function if the native implementation is absent.


## <a id="FileReader"></a>FileReader is present

The `FileReader` allows PDF.js read the file data provided in the input[type=file] HTML element. The live PDF.js demo will not be able to read local file, if the `FileReader` object is not supported.


## <a id="FileReader-readAsArrayBuffer"></a>FileReader.prototype.readAsArrayBuffer() is present

Older browsers has no `readAsArrayBuffer` method implementation: the `readAsBinaryString` will be used to emulate its functionality.


## <a id="XMLHttpRequest-overrideMimeType"></a>XMLHttpRequest.prototype.overrideMimeType() is present

The empty `overrideMimeType` method will be added to the `XMLHttpRequest.prototype`, if the browser does not support it.


## <a id="XMLHttpRequest-response"></a>XMLHttpRequest.prototype.response is present

The `response` getter will be added to the `XMLHttpRequest.prototype`, if the browser does not support it.
This is important for retrieving the binary PDF data using XHR.


## <a id="bota"></a>btoa() is present

The `btoa` will be added to the window object, if the browser does not support it.


## <a id="Function-bind"></a>Function.prototype.bind is present

The `bind` method will be added to the `Function.prototype`, if the browser does not support it.


## <a id="dataset"></a>dataset is present for HTML element

The `dataset` property will be added to the `HTMLElement.prototype`, if the browser does not support it.
This is important for specifying addition information (e.g. for test selection layer)
attached to specific HTML DOM element.


## <a id="classList"></a>classList is present for HTML element

The `classList` property will be added to the `HTMLElement.prototype`, if the browser does not support it.
This is important to simplify the viewer implementation.


## <a id="console"></a>console object is present

The `console` object will be added to the window object with empty `log` and `error` methods,
if the browser does not support it. This is important for output of the error message.


## <a id="console-log-bind"></a>console.log is a bind-able function

The `console.log` and `.error` functions will be replaced, if the browser does not allow to use
the bind method with these functions.


## <a id="navigator-language"></a>navigator.language is present

The language getter will be added to the window.navigator object, if the browser does not support it.


## <a id="fillRule-evenodd"></a>evenodd fill rule is supported

Some PDF content is using "even-odd" fill rule/method. The content will not be displayed
properly if this function is not supported.

## <a id="dash-array"></a>dashed lined is supported

Some PDF content is using custom dash line styles. The content will not be displayed
properly if this function is not supported.


## <a id="font-face"></a>@font-face is supported/enabled

Most of PDF documents are using embedded fonts. If the browser does not support `@font-face`
style rule, the document will not be displayed property.


## <a id="font-face-sync"></a>@font-face data URLs are loaded synchronously

The PDF.js shall wait some time before using fonts with CANVAS,
if the browser cannot load custom fonts  synchronously via `@font-face` that are specified as data URLs.


## <a id="Worker"></a>Worker is supported/enabled

The PDF.js will execute all code (even long running) on the main thread,
if the browser does not support web workers. 

## <a id="Worker-Uint8Array"></a>Worker can receive/send typed arrays

The PDF.js will execute all code on the main thread,
if the browser cannot send (large) typed arrayed to web workers. 

