You can choose to use a pre-built version of PDF.js or build PDF.js from source.

## Pre-built PDF.js
### With npm

This works by loading the file `pdfjs-dist/build/pdf.js` after you have installed PDF.js using:

    npm install pdfjs-dist

#### With Browserify or Webpack

If you use Browserify or Webpack there is an easy way to require the files:

```javascript
// In your Webpack config:
//
// Install `npm install url-loader` first.
// This will enable you to get the url of the worker and the pdf to use in the index.js.
// Notice that for the build process it might need some extra work.
webpackConfig.module.loaders = {
    test: /\.pdf$|pdf\.worker\.js$/,
    loader: "url-loader?limit=10000"
}

// in index.js
require('pdfjs-dist/build/pdf');
require('pdfjs-dist/web/pdf_viewer'); // Only if you need `PDFJS.PDFViewer`
// Webpack returns a string to the url because we configured the url-loader.
PDFJS.workerSrc = require('pdfjs-dist/build/pdf.worker.js');
var url = require('assets/books/my book.pdf'); 
PDFJS.getDocument(url).then(function(pdf) {/* Continue the normal tutorial from the README.*/})
```

### From examples
When the source code of PDF.js changes, the [online demo](http://mozilla.github.io/pdf.js/web/viewer.html) is automatically updated. The source of all demo files can easily be accessed at https://github.com/mozilla/pdf.js/tree/gh-pages. These files can also be uploaded to your server to use PDF.js to display PDF files from your website.

1. Download https://github.com/mozilla/pdf.js/archive/gh-pages.zip.
2. Extract the ZIP file (a directory called "pdf.js-gh-pages" will be created).
3. Copy the following directories to your website:
   * pdf.js-gh-pages/build/
   * pdf.js-gh-pages/web/  
   The web/ directory contains a 1 MB PDF file called "compressed.tracemonkey-pldi-09.pdf". This file is only used as an example for the demo and can safely be removed.
4. If you want to open a PDF from your website with PDF.js, simply link to the viewer and pass the location of the PDF file. For example:

    ```html
    <a href="/web/viewer.html?file=%2Fyourpdf.pdf">Open yourpdf.pdf with PDF.js</a>
    ```

## Build PDF.js from source
After cloning PDF.js, you can build PDF.js from source by running `node make generic` in Git Bash or another terminal. This will create the built PDF.js in the `build` folder, which you can upload to your server. Note that you must include `compatibility.js` in order to support browsers like IE8+.