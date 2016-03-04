At a minimum you will need Git and Node.js.

## Getting PDF.js
- Start the Git command line
- Change to a directory where you want to place PDF.js
- Run `git clone git://github.com/mozilla/pdf.js.git`

## Open PDF.js

### Option 1 - Node.js server
- Run `cd pdf.js`
- Run `gulp server`
- Open a browser and go to `http://localhost:8080/web/viewer.html`

### Option 2 - Another server
- Open a browser and go to `http://<yourserver>/pdf.js/web/viewer.html`

## Verify the regression
- Download the bad PDF and open it with the above viewer (using, for example, the Open File button in the toolbar) and verify that the PDF is broken.

## Start the bisecting process
- Mark the current version as bad using `git bisect start` and `git bisect bad`.

## Find bad commit ID

### Option 1 - Detecting version / commit of PDF.js installed in Firefox
- Open `resource://pdf.js/build/pdf.js`
- Find the commit in the line with 'PDFJS.build = '
- Find the version in the line with 'PDFJS.version = '

### Option 2 - Using Bugzilla patch
- A Bugzilla patch contains the commit information near `browser/extensions/pdfjs/content/build/pdf.js` [e.g., see https://bug871530.bugzilla.mozilla.org/attachment.cgi?id=750657, was added3d (good), will be 869b878 (bad)]

### Option 3 - Using MXR
- If you know it was good in the Beta or Aurora branch, get the bad commit ID from MXR. Find the line with 'PDFJS.build = ' and copy the value in the single quotes, e.g., 4e83123.

Aurora: http://mxr.mozilla.org/mozilla-aurora/source/browser/extensions/pdfjs/content/build/pdf.js#25

Beta: http://mxr.mozilla.org/mozilla-beta/source/browser/extensions/pdfjs/content/build/pdf.js#25

## Verify the working version
- `git checkout <commit ID that you found above>`
- Full refresh (CTRL + Shift + R) Firefox and verify that the PDF is no longer broken
- Mark it as good with `git bisect good`

## Continue bisecting
- Full refresh (CTRL + Shift + R) of the viewer in Firefox
- If the current version works, mark it using `git bisect good`
- If the current version does not work, mark it using `git bisect bad`
- Repeat the steps above until it converges to a single commit