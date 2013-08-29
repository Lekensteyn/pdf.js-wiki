# Bisecting a Regression

## At a minimum you'll need:
-git (on windows http://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git)
-a server, if you have python installed that will work

## Getting pdf.js
-startup the git command line from above
-move a directory where you want it to live, if you're using a server that isn't python go into the directory where your wwwroot is
-`git clone https://github.com/mozilla/pdf.js.git`

### Option 1 - Python Server
- `cd pdf.js/test`
- `python test.py --noDownload`
- open firefox and check http://localhost:8080/web/viewer.html goes to the pdf viewer

### Option 2 - Other Server
- go to http://<yourserver>/pdf.js/web/viewer.html

## Verify the Regression
- Download Bad PDF and save it in pdf.js/test/pdfs
- go to <url from above>?file=../test/pdfs/<name of pdf> and verify the PDF works

## Start the bisecting process
- Mark the current version is bad using `git bisect start` and `git bisect bad`

## Now find bad commit id

### Option 1 - Detecting version / commit of the pdf.js installed in the Firefox
- Open resource://pdf.js/build/pdf.js
- Find commit in the line with 'PDFJS.build = '
- Find version in the line with 'PDFJS.version = '

### Option 2 - Using bugzilla patch
- A bugzilla patch contains the commits information near '
browser/extensions/pdfjs/content/build/pdf.js'
 [e.g. see https://bug871530.bugzilla.mozilla.org/attachment.cgi?id=750657, was added3d (good), will be 869b878 (bad)]

### Option 3 - Using MXR
- If you know it was good in beta or aurora get the bad commit id from mxr
Find the line with 'PDFJS.build = ' and copy the value in the single quotes e.g. 4e83123
auora - http://mxr.mozilla.org/mozilla-aurora/source/browser/extensions/pdfjs/content/build/pdf.js#24
beta - http://mxr.mozilla.org/mozilla-beta/source/browser/extensions/pdfjs/content/build/pdf.js#24

## Verify the Working Version
- `git checkout <commit id that you found above>`
- Full refresh(ctr+shift+r) Firefox and verify the PDF no longer works.
- Mark it as good `git bisect good`

## Continue bisecting
- Full refresh(ctr+shift+r) of the viewer in Firefox
- If the current version works `git bisect good`
- If it fails `git bisect bad`
- Repeat same steps as above if it's bad `git bisect bad` if it's good `git bisect good`
