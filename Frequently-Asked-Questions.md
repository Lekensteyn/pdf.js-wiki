* [Can I specify a different PDF in the default viewer?](#file)
* [Can I load a PDF from another server (cross domain request)?](#faq-xhr)
* [Which browsers are supported?](#faq-support)
* [Which browsers have extensions (and where can I find install procedures)?](#faq-extensions)
* [I know JavaScript and want to contribute to the project. How do I start?](#faq-contrib)
* [Is it possible to add annotations to a PDF?](#faq-annotations)
* [What are the PDF.js keyboard shortcuts?](#faq-shortcuts)
* [The PDF.js files are too big. Is it possible to obtain minified versions of the JS files?](#minified)
* [Is there a pre-built version PDF.js available?](#gh-pages)
* [What is the ECCN for PDF.js?](#eccn)
* [PDF.js does not render my files right. Can I report an issue?](#issue)
* [I know that my PDFs are corrupted. Will PDF.js attempt to display it?](#corrupted-pdf)
* [I have a really great idea. Where is the best place to record it?](#idea)
* [I'm developing a custom solution based on PDF.js core library. Can you help me?](#custom)
* [I want to render all 100 pages in a document at a high resolution. Is it a good idea?](#allthepages)
* [PDF.js is fetching the entire PDF file from a server. Can it fetch only the required portions for rendering?](#range)
* [What is a latest stable version of PDF.js?](#version)
* [What types of PDF files are slow in PDF.js? Can I optimize a PDF file to make PDF.js faster?](#optimize)

<a name="file"></a>
## Can I specify a different PDF in the default viewer?
You can modify the `defaultUrl` app option in the `web/app_options.js` file or you can append the `?file=` query string to the viewer URL, e.g. `http://mozilla.github.com/pdf.js/web/viewer.html?file=compressed.tracemonkey-pldi-09.pdf`. In the latter case, the PDF path/URL must be encoded using `encodeURIComponent()`.

The viewer can be started without any PDF loaded by setting the `defaultUrl` app option to an empty string or by using the `?file=` query string without any location specified. Use `PDFViewerApplication.open(file)` to load the PDF file later.

You can use raw binary data to open a PDF document: use Uint8Array instead of URL in the `PDFViewerApplication.open` call. If you have base64 encoded data, please [decode](https://developer.mozilla.org/en-US/docs/Web/API/WindowBase64/Base64_encoding_and_decoding) it first -- not all browsers have `atob` or data URI scheme support. (The base64 conversion operation uses more memory, so we recommend delivering raw PDF data as typed array in first place.)

<a name="faq-xhr"></a>
## Can I load a PDF from another server (cross domain request)?
Not by default, but it is possible.  PDF.js runs with the same permissions as any other JavaScript code, which means it cannot do cross origin requests (see [Same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy) and [an example](https://gist.github.com/3452072)).  There are some possible ways to get around this such as using [CORS](http://enable-cors.org/) (see also [unsafe headers issue](https://github.com/mozilla/pdf.js/issues/3150#issuecomment-17582371) and [Access-Control-Expose-Headers issue](https://github.com/mozilla/pdf.js/issues/4530)) or setting up a proxy on your server that will feed PDF.js the PDF file (example: https://github.com/mozilla/pdf.js/issues/1000#issuecomment-133756244). Please notice that generic/demo viewer blocks this functionality if deployed not on mozilla.github.io domain to avoid content spoofing (see https://github.com/mozilla/pdf.js/pull/6916).

<a name="faq-support"></a>
## Which browsers are supported?
The objective is to support all HTML5 compliant browsers, but since feature support varies per browser/version our support for all PDF features varies as well. We include `compatibility.js` by default which has polyfills for missing features. Find the list of features needed for PDF.js to properly work and browser tests for those features at [[Required Browser Features]]. In general, the support is below. If no version is indicated, then the latest desktop/mobile versions are intended.

<table>
  <tr><th>Browser</th><th>Supported</th><th>Automated testing</th><th>Notes</th></tr>
  <tr>
    <td>Firefox</td>
    <td>Yes</td>
    <td>Windows/Linux</td>
    <td></td>
  </tr>
  <tr>
    <td>Chrome</td>
    <td>Yes</td>
    <td>Windows/Linux</td>
    <td></td>
  </tr>
  <tr>
    <td>Opera</td>
    <td>Yes</td>
    <td>None</td>
    <td></td>
  </tr>
  <tr>
    <td>IE 11/Edge</td>
    <td>Mostly</td>
    <td>None</td>
    <td>Some missing features/defects have been reported, but no problems in general.</td>
  </tr>
  <tr>
    <td>Safari 9+</td>
    <td>Mostly</td>
    <td>None</td>
    <td>Some missing features/defects have been reported, but no problems in general. For mobile only iOS 10 and higher are supported.</td>
  </tr>
  <tr>
    <td>IE 10 and below</td>
    <td>No</td>
    <td>None</td>
    <td>Too many features are missing to be supported.</td>
  </tr>
  <tr>
    <td>Safari 8 and below</td>
    <td>No</td>
    <td>None</td>
    <td>Too many features are missing to be supported.</td>
  </tr>
  <tr>
    <td>Android 4 and below</td>
    <td>No</td>
    <td>None</td>
    <td>Too many features are missing to be supported.</td>
  </tr>
</table>

<a name="faq-extensions"></a>
## Which browsers have extensions (and where can I find install procedures)?
The Chromium extension is maintained by a PDF.js contributor. To install the Chromium extension, please refer to the [README](https://github.com/mozilla/pdf.js/blob/master/README.md).

The Firefox extension is not supported and marked as disabled for Firefox versions 35 and up. PDF.js is part of Firefox since version 19. The extension is mostly used by developers and for bringing a newer version of the PDF.js library to an older Firefox version. Users should uninstall the extension, revert the `pdfjs.disabled` configuration setting and set the `Options -> Applications` selection for PDF documents to the internal viewer to continue viewing PDF files with PDF.js in Firefox.

<a name="faq-contrib"></a>
## I know JavaScript and want to contribute to the project. How do I start?
First, you need to prepare your [fork](https://help.github.com/articlenetworks/fork-a-repo) and setup the development environment. Don't forget to read the [[Contributing]] page. Second, make yourself familiar with the [PDF format and PDF.js internals](Additional-Learning-Resources). Third, if you don't already have a certain issue you want to fix, choose one from the [open issues labeled 5-good-beginner-bug](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open).  Last, submit a [pull request](https://help.github.com/articles/using-pull-requests) for the review. _During any part of the process we recommend communicating with the PDF.js team on #pdfjs IRC channel at irc.mozilla.org if you have questions or need to find a reviewer._

<a name="faq-annotations"></a>
## Is it possible to add annotations to a PDF?
PDF.js is designed for *reading* PDF files, not editing them. Because of that we don't support adding any kind of annotations. However, we do support rendering annotations for viewing.

<a name="faq-shortcuts"></a>
## What are the PDF.js keyboard shortcuts?
(warning, the following list may be incomplete)

### Navigation
The <kbd>Home</kbd>, <kbd>End</kbd>, <kbd>Page up</kbd>, <kbd>Page down</kbd> and all arrow keys can be used to navigate the document. Moreover, the following navigation shortcuts exist:

* **Next page:** <kbd>n</kbd>, <kbd>j</kbd>, <kbd>Space bar</kbd> (presentation mode only), <kbd>Enter</kbd> (presentation mode only) or left click (presentation mode only)
* **Previous page:** <kbd>p</kbd>, <kbd>k</kbd>, <kbd>Shift</kbd> + <kbd>Space bar</kbd> (presentation mode only), <kbd>Shift</kbd> + <kbd>Enter</kbd> (presentation mode only) or <kbd>Shift</kbd> + left click (presentation mode only)

### Viewer controls
User interface buttons or <kbd>ctrl</kbd> + mouse wheel can be used to change the zooming level, but keyboard shortcuts are also available:
* **zoom in:** <kbd>ctrl</kbd> + <kbd>+</kbd>, <kbd>ctrl</kbd> + <kbd>=</kbd>
* **zoom out:** <kbd>ctrl</kbd> + <kbd>-</kbd>
* **restore normal zoom:** <kbd>ctrl</kbd> + <kbd>0</kbd>
* **rotate the document clockwise:** <kbd>r</kbd>
* **rotate counterclockwise:** <kbd>shift</kbd> + <kbd>r</kbd>
* **presentation mode:** <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>p</kbd> (does not work in IE11)
* **enable hand tool:** <kbd>h</kbd>
* **enable text selection tool:** <kbd>s</kbd>
* **move focus to the 'go to page' box:** <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>g</kbd>

(replace ctrl with meta on some configurations)

### Outline sidebar

- After showing the sidebar, click on the "Show document outline" button (![Show document outline](https://mozilla.github.io/pdf.js/web/images/toolbarButton-viewOutline.png)) to show the document outline (if the PDF file has one).
- Nested outline items can be expanded/collapsed by clicking on the triangles at the left of an item.
- To expand/collapse all items under the selected item, press <kbd>Shift</kbd> while clicking on the triangle.
- Double-click on the "Show document outline" button (![Show document outline](https://mozilla.github.io/pdf.js/web/images/toolbarButton-viewOutline.png)) to expand/collapse all outline items.

<a name="minified"></a>
## The PDF.js files are too big. Is it possible to obtain minified versions of the JS files?

You can build a minified version of PDF.js using the following command:

`gulp minified`

We use UglifyJS to minify the JS files. It is known that other minifiers might break PDF.js code if advanced options are used (see [#710](https://github.com/mozilla/pdf.js/issues/710) or [#2479](https://github.com/mozilla/pdf.js/issues/2479)). It's safe to use minifiers, such as Google Closure Compiler, in whitespace/comments removal mode.

<a name="gh-pages"></a>
## Is there a pre-built version PDF.js available?

Yes. Please see http://mozilla.github.io/pdf.js/getting_started/ page for details. Also the code for the website at http://mozilla.github.io/pdf.js is located in the "gh-pages" branch. You can clone it using `git clone -b gh-pages https://github.com/mozilla/pdf.js.git pdfjs-gh-pages` or download [the archive](https://github.com/mozilla/pdf.js/archive/gh-pages.zip).

There are also generic PDF.js library builds available at https://github.com/mozilla/pdfjs-dist. These builds can be installed via npm `npm install pdfjs-dist` or bower `bower install pdfjs-dist`.

<a name="eccn"></a>
## What is the ECCN for PDF.js?

PDF.js is publicly available software not subject to the Export Administration
Regulations (EAR) per EAR 734.3(b) and 734.7. Because PDF.js is not subject to
the EAR it does not have an Export Control Classification Number (ECCN).
Mozilla has completed the notification for PDF.js publicly available encryption
source code per EAR 742.15(b).

<a name="issue"></a>
## PDF.js does not render my files correctly. Can I report an issue?

Yes. The issues are used to track both bugs filed by users and specific work items for developers. Try to file one issue per problem observed.

Please specify valid title (e.g. "Glyph spacing is incorrect" instead of "PDF.js does not work") and provide more details about the issue: link to the PDF, location in the PDF, screenshot, browser version, operating system, PDF.js version and JavaScript console warning/error messages. The issues that do not have enough details provided will be closed as invalid/incomplete.

<a name="corrupted-pdf"></a>
## I know that my PDFs are corrupted. Will PDF.js attempt to display it?

Yes. PDF.js will attempt to recover usable PDF data (pages, content or fonts) and display the document. Please report the issue (see above) and we will take a look.

<a name="idea"></a>
## I have a really great idea. Where is the best place to record it?

You can contact the developers on our IRC channel `#pdfjs` on `irc.mozilla.org`.

The issue tracking system is designed to record a single technical problem. A bug report is something a developer/contributor can work on. The [GitHub issue tracker](https://github.com/mozilla/pdf.js/issues?state=open) is not a good place for general, not well thought out or unworkable ideas. Most likely a discussion-type issue will not be addressed for a long time or closed as invalid.

<a name="custom"></a>
## I'm developing a custom solution based on PDF.js core library. Can you help me?

We are glad to hear that and will try to help you, but first check the examples at https://github.com/mozilla/pdf.js#learning and search existing [issues](https://github.com/mozilla/pdf.js/search?q=keyword&type=Issues). If this does not help, please prepare short well-documented example that demonstrates the problem and make it accessible online on your website, JSBin, etc. before opening a new issue or contacting us on the IRC channel -- keep in mind that just code snippets won't help us troubleshoot the problem. Issues that do not provide enough details will be closed as invalid/incomplete (see [reporting issue](#issue) above).

<a name="allthepages"></a>
## I want to render all 100 pages in a document at a high resolution. Is it a good idea?

Not really. You can count yourself: a letter page size is 816⨉1056px at 96DPI (and if you have a HiDPI display, multiply each dimension by `window.devicePixelRatio`, e.g., 2), so you will need a canvas that takes up 816⨉1056⨉4 = 3,446,784 bytes (don't forget to multiply that by e.g., 2⨉2 = 4 if it's a HiDPI display). This requires you to allocate 3.5Mb (or 14Mb) per page. You need a decent amount of memory to hold the 100 canvases, and it does not count the time that is spent on rendering them.

The demo viewer creates, renders, and holds canvases only for visible pages to reduce the amount of used memory. Our recommendation is to create and render only visible pages.

<a name="range"></a>
## PDF.js is fetching the entire PDF file from a server. Can it fetch only the required portions for rendering?

Actually, PDF.js is doing just that. PDF is a complicated format; in most of the cases, the vital data of a PDF document is located at the end. Depending on [browser support](#faq-support) and on what web server returns the [HTTP Range Requests headers](https://tools.ietf.org/html/rfc7233), PDF.js may automatically start using HTTP Range Requests to fetch not-yet-loaded portions of a PDF needed for rendering visible pages, so a document can be rendered without fully loading it.

<a name="version"></a>
## What is a latest stable version of PDF.js?

PDF.js is a general-purpose library to parse and render PDFs. It is included in a number of projects such as Firefox, a Chromium extension, et cetera. We are recording changes to the library with GitHub [pull requests](https://github.com/mozilla/pdf.js/pulls). The changelog is also available from the Git log.

The version number consists of three digits: the major release number, minor release number and build number. Before version 1.2, the major and minor numbers were selected when some major milestone was reached. Currently, we are using semantic versioning, where a major version release means that we can introduce API-breaking changes and a minor version release indicates added functionality and backwards compatible changes. The build number is incremented by one each time a new commit is pushed to the master branch. As a sanity check, we accompany each version number with the SHA hash of the latest commit.

We are moving fast and trying to land as much good stuff as we can review and test. The [generic viewer](http://mzl.la/pdf-js) always contains the latest PDF.js build and is available for testing.

During cooldown period, about once or twice in 6 weeks, we push our library to the [Firefox Nightly](http://nightly.mozilla.org/) channel. We decided to tag/mark our master branch each time we do that, and at this point a beta release is created. To promote a latest beta to a stable release, we listen for feedback (via [GitHub](https://github.com/mozilla/pdf.js/issues), [Bugzilla](https://bugzilla.mozilla.org/enter_bug.cgi?product=Firefox&component=PDF+Viewer) or [IRC](irc://irc.mozilla.org/%23pdfjs)) from the users and projects that use the PDF.js library. If no critical issues (e.g. a build is unusable, majority of the documents cannot be rendered, etc.) appeared, we promote the build as stable. Otherwise we either discard the release by replacing it by new beta or redo the build with commits that fix a critical issue.

<a name="optimize"></a>
## What types of PDF files are slow in PDF.js? Can I optimize a PDF file to make PDF.js faster?

Typically, PDFs with a smaller file size will be rendered faster and it depends on how big a single page is. The amount of pages does not affect the performance. It's essential that you optimize your documents for the web. See [Optimize a PDF](https://helpx.adobe.com/acrobat/using/optimizing-pdfs-acrobat-pro.html) from Adobe's website for more information. There are more improvement techniques that we can suggest:

  1. Avoid using high resolution images -- 150 dpi resolution for scanned images shall be enough for screens, especially for low powered devices;
  2. Try to use JPEG encoding for color images/photos in RGB colorspace when possible;
  3. Avoid using expensive compositions/effects such as transitions/masking -- flatten transparency;
  4. Avoid using PDF generators (or don't create content) that produce ineffective PDF output (e.g. LibreOffice creates a lots of tiny images for vector elements/pictures it does not understand);
  5. If there is such a setting, use web-optimized PDF output / linearization;
  6. Fix or don't produce corrupted PDFs that do not conform to the PDF32000 specification.