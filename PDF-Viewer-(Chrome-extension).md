<img align="left" src="https://mozilla.github.io/pdf.js/images/logo.svg"> The PDF Viewer is a Chrome extension that displays PDF files using PDF.js.  
Install it from https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm .

## End-user documentation

### Shortcuts
See [What are the PDF.js keyboard shortcuts?](Frequently-Asked-Questions#faq-shortcuts)

### Preferences
Visit `chrome://extensions/?options=oemmndcbldboiebfnladdacbdfmadadm` to change the default settings, such as whether to enable the hand tool by default, or to enable tools for [debugging PDF.js](Debugging-pdf.js).

By default, the extension is disabled in incognito mode and on local files. Visit `chrome://extensions/?id=oemmndcbldboiebfnladdacbdfmadadm` and click on "Allow in incognito" to allow PDF files to be viewed in incognito mode, and "Allow access to file URLs" to allow local PDF files to be viewed.

Administrators can also use Group policies to set the default settings for deployment in an educational or enterprise environment. See https://github.com/mozilla/pdf.js/pull/5082 for documentation.

## Report an issue
Found a defect? Open a new issue and include a clear description of the problem (see https://github.com/mozilla/pdf.js/blob/master/CONTRIBUTING.md).

There is also a support page at the Chrome Web Store (https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm/support), but it's not read very often due to the lack of notifications.

## Privacy policy

As of version 1.5.285, the extension sends at most two pings a day to pdfjs.robwu.nl so that the developers know which versions of Chrome we need to take into account. The source code and privacy policy are published at https://github.com/Rob--W/pdfjs-telemetry.

## Release process
[Rob Wu (@Rob--W)](https://github.com/Rob--W) maintains the Chrome extension and manages its listing in the Chrome Web Store. Contact him for questions about the extension (e.g. "When will the PDF Viewer be updated?").

The release process is as follows:

1. Update the [cws-release@Rob--W branch](https://github.com/Rob--W/pdf.js/tree/cws-release) to the master branch.
2. Apply extra patches on top of the cws-release. This is only done for (critical) bugs that impact the usability of the PDF viewer.
3. Build and test the extension.
4. Look at the user feedback at the [Chrome Web Store support page](https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm/support) and check whether the bugs are fixed.
4. Upload to the Chrome Web Store dashboard.
5. Push changes to [cws-release@Rob--W branch](https://github.com/Rob--W/pdf.js/tree/cws-release), tag the release at https://github.com/Rob--W/pdf.js/releases and respond to bugs reports on PDF.js's issue tracker and the [Chrome Web Store support page](https://chrome.google.com/webstore/detail/pdf-viewer/oemmndcbldboiebfnladdacbdfmadadm/support).