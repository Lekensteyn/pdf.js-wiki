This page shows you how to render a PDF with text-selection enabled. To get the minimal example working, I extracted the parts relevant to text-selection from viewer.js. The text-selection code in viewer.js supports operations like text-search and match, but this minimal example does not. The reason is that the text-search and match operations depend on some view-specific components (like the find bar) in viewer.js and will not work in this minimal example. At some point in the future, the text-selection, search, and match operations can be pulled out of viewer.js into their own class. Then all these operations can be abstracted and exposed via an API. This example is also available in the examples directory. 

For this example, we are going to be using a sample PDF that is available [here](http://vivin.net/pub/pdfjs/TestDocument.pdf) However, we will not be loading up this document directly in this example. Instead, we will be starting with the base64 representation of the PDF. Of course, if you have the PDF file at your disposal you can simply do `PDFJS.getDocument('mypdf.pdf').then(...)` instead of using the base64-encoded data.

First, let's take a look at the HTML file that we're going to use at https://github.com/mozilla/pdf.js/blob/master/examples/text-selection/index.html, which includes necessary scripts (including minimal.js described below).

There are a few resources that we use. The first is a CSS file called `minimal.css`. This contains the minimal CSS styles required to get text-selection to work. Text-selection is accomplished by overlaying `div`s over the PDF. These `div`s will contain text that matches the PDF text that they are overlaying. `minimal.css` looks like this:

```css
body {
    font-family: arial, verdana, sans-serif;
}

.pdf-content {
    border: 1px solid #000000;
}

/* CSS classes used by TextLayerBuilder to style the text layer divs */

/* This stuff is important! Otherwise when you select the text, the text in the divs will show up! */
::selection { background:rgba(0,0,255,0.3); }
::-moz-selection { background:rgba(0,0,255,0.3); }

.textLayer {
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    color: #000;
    font-family: sans-serif;
    overflow: hidden;
}

.textLayer > div {
    color: transparent;
    position: absolute;
    line-height: 1;
    white-space: pre;
    cursor: text;
}

.textLayer .highlight {
    margin: -1px;
    padding: 1px;

    background-color: rgba(180, 0, 170, 0.2);
    border-radius: 4px;
}

.textLayer .highlight.begin {
    border-radius: 4px 0px 0px 4px;
}

.textLayer .highlight.end {
    border-radius: 0px 4px 4px 0px;
}

.textLayer .highlight.middle {
    border-radius: 0px;
}

.textLayer .highlight.selected {
    background-color: rgba(0, 100, 0, 0.2);
}
```

The next resources that we have is `pdf.js` itself (be sure you run `node make generic` to build it) and few additional JavaScript files:

```html
<script src="../../web/pdf_find_bar.js"></script>
<script src="../../web/pdf_find_controller.js"></script>
<script src="../../web/ui_utils.js"></script>
<script src="../../web/text_layer_builder.js"></script>
```

Finally we have `minimal.js`, which contains all the logic required to actually load, render, and enable text-selection on the PDF. The code is well-commented, so you should be able to easily see what is going on at https://github.com/mozilla/pdf.js/blob/master/examples/text-selection/js/minimal.js, the following code snippet retrieves the text content and builds the text layer:

```javascript
// ...
    page.getTextContent().then(function (textContent) {
      var textLayer = new TextLayerBuilder({
        textLayerDiv: $textLayerDiv.get(0),
        viewport: viewport,
        pageIndex: 0
      });
      textLayer.setTextContent(textContent);

      // ...
    });
// ...
```
 
