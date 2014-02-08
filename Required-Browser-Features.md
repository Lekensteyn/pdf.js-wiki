The page describes the features that are required for a web browser to have PDF.js function properly. Some of the features are critical and does not let PDF.js function properly if they are not supported or disabled. Some of them can be emulated if absent (e.g. in the [compatibility.js](https://github.com/mozilla/pdf.js/blob/master/web/compatibility.js) file), however the PDF.js performance and memory usage will be worse than when the feature is present.

The required features tests can be run at http://mozilla.github.com/pdf.js/features/

## <a id="canvas"></a>CANVAS element is present

Support of the CANVAS element and 2D context is required feature for PDF.js.
No emulation of the CANVAS element is provided for the browsers that do not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="get-literal"></a>get-literal properties

The core library defines object properties using object 'get' literal:

```
var obj = {
  get prop() { return 1; }
};
```

The browsers that don't understand this syntax will not be able to execute the code.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="addEventListener"></a>addEventListener is present

The `addEventListener` method is used to bind event listeners for DOM elements.
No emulation of the `addEventListener` method is provided in the browsers that do not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="Uint8Array"></a><a id="Uint16Array"></a><a id="Int32Array"></a><a id="Float32Array"></a><a id="Float64Array"></a>Typed arrays are present

The `Uint8Array`, `Uint16Array`, `Int32Array`, `Uint32Array`, `Float32Array` and `Float64Array` will be replaced by the artificial TypedArray object if those types are not implemented natively.

Only `subarray`, `buffer`, `set` and `byteLength` are similated. The `subarray` just clones the array. The `set` method is provided to emulate the `Uint8Array`'s `set` method. The emulated typed arrays are slower, don't truncate the items to specific data types and are memory inefficient.

If the `Float32Array` native implementation exists and the `Float64Array` is absent, then the `Float32Array` will be used instead of `Float64Array`.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="Object-create"></a>Object.create() is present

The `Object.create` method will be added to the `Object` function if the native implementation is absent.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="Object-defineProperty"></a>Object.defineProperty() is present


The `Object.defineProperty` method will be added to the `Object` function if the native implementation is absent. The `__defineGetter__` / `__defineSetter__` will be used instead.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="Object-defineProperty-DOM"></a>Object.defineProperty() can be used with DOM objects

Some browsers do not allow using the `Object.defineProperty` with DOM objects.
In this case, the `Object.defineProperty` is replaced by the artificial one. See [Object.defineProperty() is present](#Object-defineProperty).

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="get-literal-redefine"></a>Defined via get-literal properties can be redefined

Some browsers does not allow redefine properties defined with get literal by the `Object.defineProperty`.
In this case, the `Object.defineProperty` is replaced by the artificial one. See [Object.defineProperty() is present](#Object-defineProperty).

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="Object-keys"></a>Object.keys() is present

The `Object.keys` method will be added to the `Object` function if the native implementation is absent.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="FileReader"></a>FileReader is present

The `FileReader` allows PDF.js read the file data provided in the input[type=file] HTML element. The live PDF.js demo will not be able to read a local file, if the `FileReader` object is not supported.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.6.0)</td>
    </tr>
  </tbody>
</table>

## <a id="FileReader-readAsArrayBuffer"></a>FileReader.prototype.readAsArrayBuffer() is present

Older browsers that have no `readAsArrayBuffer` method implementation: the `readAsBinaryString` will be used to emulate its functionality.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.7)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.6.0)</td>
    </tr>
  </tbody>
</table>

## <a id="XMLHttpRequest-overrideMimeType"></a>XMLHttpRequest.prototype.overrideMimeType() is present

The empty `overrideMimeType` method will be added to the `XMLHttpRequest.prototype`, if the browser does not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Emulated (v.10)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="XMLHttpRequest-response"></a>XMLHttpRequest.prototype.response is present

The `response` getter will be added to the `XMLHttpRequest.prototype`, if the browser does not support it.
This is important for retrieving the binary PDF data using XHR.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>No</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>No</td>
    </tr>
  </tbody>
</table>

## <a id="bota"></a>btoa() is present

The `btoa` will be added to the window object, if the browser does not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="Function-bind"></a>Function.prototype.bind is present

The `bind` method will be added to the `Function.prototype`, if the browser does not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="dataset"></a>dataset is present for HTML element

The `dataset` property will be added to the `HTMLElement.prototype`, if the browser does not support it.
This is important for specifying addition information (e.g. for text selection layer)
attached to specific HTML DOM element.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Emulated (v.10)<br>
          Yes (v.11)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="classList"></a>classList is present for HTML element

The `classList` property will be added to the `HTMLElement.prototype`, if the browser does not support it.
This is important to simplify the viewer implementation.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="console"></a>console object is present

The `console` object will be added to the window object with empty `log` and `error` methods,
if the browser does not support it. This is important for the output of error messages and diagnostic information.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="console-log-bind"></a>console.log is a bind-able function

The `console.log` and `console.error` functions will be replaced, if the browser does not allow using
the bind method with these functions.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="apply-typed-array"></a>Function.prototype.apply accepts typed array

The core code relies on the `Function.prototype.apply` method to accept the typed array as the second argument.
No emulation is provided in browsers that do not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
      <td>?</td>
    </tr>
  </tbody>
</table>

## <a id="navigator-language"></a>navigator.language is present

The language getter will be added to the window.navigator object, if the browser does not support it.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Emulated (v.10)<br>
          Yes (v.11)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="fillRule-evenodd"></a>evenodd fill rule is supported

Some PDF content is using "even-odd" fill rule/method. The content will not be displayed
properly (example: [#2351](https://github.com/mozilla/pdf.js/issues/2351)) if this feature is not supported.  

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>No (v.25)</td>
      <td>Yes (v.7)</td>
      <td>No (v.10)</td>
      <td>?</td>
      <td>No (v.6.0)</td>
    </tr>
  </tbody>
</table>

## <a id="dash-array"></a>dashed line style is supported

Some PDF content is using custom dash line styles. The content will not be displayed
properly if this feature is not supported.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.7)</td>
      <td>No (v.10)</td>
      <td>?</td>
      <td>No (v.6.0)</td>
    </tr>
  </tbody>
</table>

## <a id="font-face"></a>@font-face is supported/enabled

Most of PDF documents use embedded fonts. If the browser does not support `@font-face`
style rule, the document will not be displayed property.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="font-face-sync"></a>@font-face loading completion detection

The PDF.js shall wait some time before using fonts with CANVAS,
if the browser cannot tell if fonts are loaded and can be used.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Emulated (v.25)</td>
      <td>Yes (v.14)</td>
      <td>Yes (v.9)</td>
      <td>?</td>
      <td>Yes (v.6)</td>
    </tr>
  </tbody>
</table>

## <a id="TextDecoder"></a>TextDecoder is supported

Some East Asian PDFs will be completely garbled, if the browser does not support the `TextDecoder`. See http://encoding.spec.whatwg.org/

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>No (v.24)</td>
      <td>Yes (v.18)</td>
      <td>No (v.10)</td>
      <td>?</td>
      <td>No (v.6)</td>
    </tr>
  </tbody>
</table>

## <a id="Worker"></a>Worker is supported/enabled

The PDF.js will execute all code (even long running) on the main thread,
if the browser does not support web workers. 

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5)</td>
    </tr>
  </tbody>
</table>

## <a id="Worker-Uint8Array"></a>Worker can receive/send typed arrays

The PDF.js will execute all code on the main thread,
if the browser cannot send (large) typed arrays to web workers. 

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.6)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.6.0)</td>
    </tr>
  </tbody>
</table>


## <a id="Worker-transfers"></a>Worker can use transfers for postMessage

Checks if the browser can transfer large chunks of data to the main thread vs cloning typed arrays. See [Using web workers](https://developer.mozilla.org/en-US/docs/Web/Guide/Performance/Using_web_workers#Passing_data_by_transferring_ownership_%28transferable_objects%29)

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.17)</td>
      <td>Yes (v.18~27)</td>
      <td>No (v.11)</td>
      <td>?</td>
      <td>?</td>
    </tr>
  </tbody>
</table>

## <a id="Worker-xhr-response"></a>XMLHttpRequest supports the response property in web workers

The PDF.js will execute all code on the main thread,
if the browser cannot request network binary data from web workers. 

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yes (v.24)</td>
      <td>Yes (v.10)</td>
      <td>Yes (v.10)</td>
      <td>?</td>
      <td>Yes (v.5.1)</td>
    </tr>
  </tbody>
</table>

## <a id="Worker-TextDecoder"></a>TextDecoder is supported in web workers

Texts will not be copied properly on some East Asian PDFs. If the browser does not support the `TextDecoder` in web workers, the `FileReaderSync` will be used instead.

<table>
  <thead>
    <tr>
      <th>Chrome</th>
      <th>Firefox (Gecko)</th>
      <th>Internet Explorer</th>
      <th>Opera</th>
      <th>Safari</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Emulated (v.24)</td>
      <td>Yes (v.20)</td>
      <td>Emulated (v.10)</td>
      <td>?</td>
      <td>No (v.6)</td>
    </tr>
  </tbody>
</table>
