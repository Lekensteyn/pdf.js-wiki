You can choose to use a pre-built version of PDF.js, or build PDF.js from source.

## Pre-built PDF.js
### With npm

This way works by loading this file `pdfjs-dist/build/pdf.js` after you install pdf.js:

    npm install pdfjs-dist

#### With webpack/browserify

If you use webpack or browserify there is an easy way to require the files:

   var pdf = require('pdfjs-dist/build/pdf');
   var pdfWorker = require('pdfjs-dist/build/pdf.worker');
   // Still figuring out how to use with worker.

### From examples
When the source code of PDF.js changes, the [online demo](http://mozilla.github.io/pdf.js/web/viewer.html) is automatically updated. The source of all demo files can easily be accessed at https://github.com/mozilla/pdf.js/tree/gh-pages/.  
These files can also be uploaded to your server to use PDF.js to display PDF files from your website

1. Download https://github.com/mozilla/pdf.js/archive/gh-pages.zip.
2. Extract the zip file (a directory called "pdf.js-gh-pages" will be created).
3. Copy the following directories to your website:
   * pdf.js-gh-pages/build/
   * pdf.js-gh-pages/web/  
   The web/ directory contains a 1 MB pdf file called "compressed.tracemonkey-pldi-09.pdf". This file is only used as an example for the demo and can safely be removed if you need disk space.
4. If you want to open a PDF from your website with PDF.js, simply link to the viewer and pass the location of the PDF file. For example:

    ```html
    <a href="/web/viewer.html?file=%2Fyourpdf.pdf">Open yourpdf.pdf with PDF.js</a>
    ```

## Build PDF.js from source
### Linux
* [Instructions for Linux can be found here.](Setup-PDF.js-in-a-website-(Linux))

### Windows
* [Instructions for Windows can be found here.](Setup-PDF.js-in-a-website-(Windows))