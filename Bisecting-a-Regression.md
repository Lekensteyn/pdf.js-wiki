The minimum requirements are Git and Node.js.

## Clone PDF.js
- Open the Git command line.
- Change to a directory where you want to place PDF.js.
- Run `git clone git://github.com/mozilla/pdf.js.git`.

## Start PDF.js

### Using Node.js
- Run `cd pdf.js`.
- Run `gulp server`.
- Open a browser and visit `http://localhost:8080/web/viewer.html`.

### Using another server
- Open a browser and go to `http://<yourserver>/pdf.js/web/viewer.html`.

## Verify the regression
Download the bad PDF and open it with the above viewer (using, for example, the "Open File" button in the toolbar) and verify that rendering the PDF is broken.

## Start the bisection process
Mark the current version as bad using `git bisect start` and `git bisect bad`.

## Find the bad commit ID

### Using the commit/version of PDF.js installed in Firefox
- Open `resource://pdf.js/build/pdf.js`.
- Find the commit in the line with `PDFJS.build =`.
- Find the version in the line with `PDFJS.version =`.

### Using a Bugzilla patch
A Bugzilla patch contains the commit information near `browser/extensions/pdfjs/content/build/pdf.js`, e.g., see https://bug871530.bugzilla.mozilla.org/attachment.cgi?id=750657 (was added3d (good), will be 869b878 (bad)).

### Using DXR
-f you know it was good in the Beta branch, get the bad commit ID from DXR. Find the line with `PDFJS.build =` and copy the value in the single quotes, for example `4e83123`. You can find PDF.js on DXR at http://dxr.mozilla.org/mozilla-beta/source/browser/extensions/pdfjs/content/build/pdf.js.

## Verify the working version
- Run `git checkout <commit ID that you found above>`.
- Do a full refresh (CTRL + Shift + R) Firefox and verify that rendering of the PDF is no longer broken.
- Mark it as good with `git bisect good`.

## Continue bisecting
- Do a full refresh (CTRL + Shift + R) of the viewer in Firefox.
- If the current version works, mark it using `git bisect good`.
- If the current version does not work, mark it using `git bisect bad`.
- Repeat the steps above until it converges to a single commit.