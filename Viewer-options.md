Options for pdf.js's viewer that can be given at the URL level.  This page is current as of 2013 April 21.

Multiple values of either type can be combined by separating with an ampersand (&) including after the hash (Example: #page=2&textLayer=off).

Options after the ?
Example: http://www.example.com/pdf.js?file=myfile.pdf
* file: pdf filename to use (must be on the same server due to javascript limitations).  Example: file=myfile.pdf

Options after the #
Example: http://www.example.com/pdf.js#page=2
* page: page number.  Example: page=2
 * zoom: zoom level.  Example: zoom=200
* nameddest: go to a named destionation
* pagemode: either "thumbs" or "bookmarks".  Example: pagemode=thumbs
* disableWorker: set to true to disable web workers.  Example: disableWorker=true
* disableRange: set to true to disable... something
* disableAutoFetch: set to true to disable... something
* locale: set a localization
* textLayer: set to one of the following. Example: textLayer=off
 * off: disable textLayer generation
 * visible, shadow, hover: apply the css class textlayer-<value> to all text layers.
* pdfBug: handle pdf bugs