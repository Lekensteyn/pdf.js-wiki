You can choose to use a pre-built version of PDF.js or build PDF.js from source.

## Pre-built PDF.js
### With npm

Add the dependencies to your project:

    npm install pdfjs-dist --save

You can find a usage example at https://github.com/mozilla/pdf.js/blob/master/examples/node/getinfo.js.

#### With Webpack

Add the dependencies to your project:

    npm install pdfjs-dist --save-dev

To use the library in your project add `require('pdfjs-dist')` to your file requires and build your project normally. The worker shall be built into a separate bundle: take the file "./node_modules/pdfjs-dist/build/pdf.worker.entry.js" or built a separate file that uses `require('pdfjs-dist/build/pdf.worker')`. `PDFJS.workerSrc` shall be set to point to this file. You can use the `pdfjs-dist/webpack` module for PDF.js autoconfiguration.

Refer to https://github.com/mozilla/pdf.js/tree/master/examples/webpack for a complete example.

#### With Browserify

Add the dependencies to your project:

    npm install pdfjs-dist --save-dev

To use the library in your project add `require('pdfjs-dist')` to your file requires and build your project normally. The worker shall be built into a separate bundle: take the file "./node_modules/pdfjs-dist/build/pdf.worker.entry.js" or built a separate file that uses `require('pdfjs-dist/build/pdf.worker')`. `PDFJS.workerSrc` shall be set to point to this file.

Refer to https://github.com/mozilla/pdf.js/tree/master/examples/browserify for a complete example.

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

The viewer is built on the display layer and is the UI for PDF viewer in Firefox and the other browser extensions within the project. It can be a good starting point for building your own viewer. *However, we do ask if you plan to embed the viewer in your own site, that it not just be an unmodified version. Please re-skin it or build upon it.*

## Build PDF.js from source
After cloning PDF.js, you can build PDF.js from source by running `gulp generic` in Git Bash or another terminal. This will create the built PDF.js in the `build` folder, which you can upload to your server.