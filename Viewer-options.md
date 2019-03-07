Below are the options for the PDF.js viewer that can be given at URL level. Multiple values of either type can be combined by separating with an ampersand (`&`) after the hash (for example: `#page=2&zoom=200`).

## Options after the \#
Example: https://mozilla.github.io/pdf.js/web/viewer.html#page=2

* page: page number. Example: page=2
* zoom: zoom level. Example: zoom=200 (accepted formats: `[zoom],[left offset],[top offset]`, `page-width`, `page-height`, `page-fit`, `auto`)
* nameddest: go to a named destination
* pagemode: either "thumbs" or "bookmarks".  Example: pagemode=thumbs

## Options after the ?
Example: https://mozilla.github.io/pdf.js/web/viewer.html?file=compressed.tracemonkey-pldi-09.pdf

* file: the path of the PDF file to use (must be on the same server due to JavaScript limitations). Please notice that the path/URL must be encoded using encodeURIComponent(), e.g. `/viewer.html?file=%2Fpdf.js%2Fweb%2Fcompressed.tracemonkey-pldi-09.pdf`
