* [Can I specify different PDF in the default viewer?](#file)
* [Can I load a PDF from another server (cross domain request)?](#faq-xhr)
* [What browsers are supported?](#faq-support)
* [What browsers have extensions (and where can I find install procedures)?](#faq-extensions)
* [I know JavaScript and want to contribute to the project. How do I start?](#faq-contrib)
* [Is it possible to add annotations to a PDF?](#faq-annotations)
* [What are the PDF.js keyboard shortcuts?](#faq-shortcuts)
* [PDF.js files are too big. Can you provide minified versions of CSS and JS files?](#minified)
* [Is there a pre-built version PDF.js available?](#gh-pages)
* [PDF.js does not render my files right. Can I report an issue?](#issue)
* [I know that my PDFs are corrupted. Will PDF.js attempt to display it?](#corrupted-pdf)
* [I have a really great idea. Where is the best place to record it?](#idea)
* [I'm developing a custom solution based on PDF.js core library. Can you help me?](#custom)

<a name="file"></a>
## Can I specify a different PDF in the default viewer?
You can modify the `DEFAULT_URL` variable in the `web/viewer.js` file or you can append the `?file=` query string to the viewer URL, e.g. `http://mozilla.github.com/pdf.js/web/viewer.html?file=compressed.tracemonkey-pldi-09.pdf`.

<a name="faq-xhr"></a>
## Can I load a PDF from another server (cross domain request)?
Not by default, but it is possible.  PDF.js runs with the same permissions as any other JavaScript code, which means it cannot do cross origin requests (see [Same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy) and [example](https://gist.github.com/3452072)).  There are some possible ways to get around this such as using [CORS](http://enable-cors.org/) (and [unsafe headers issue](https://github.com/mozilla/pdf.js/issues/3150#issuecomment-17582371)) or setting up a proxy on your server that will feed PDF.js the PDF file. Both workarounds are out of the scope of the PDF.js project and we will not provide code to do either.

<a name="faq-support"></a>
## What browsers are supported?
The goal is to support all HTML5 compliant browsers, but since feature support varies per browser/version our support for all PDF features varies as well. If you want to support more browsers than Firefox you'll need to include [compatibility.js](https://github.com/mozilla/pdf.js/blob/master/web/compatibility.js) which has polyfills for missing features. Find the list of features needed for PDF.js to properly work and browser tests for those features at [[Required Browser Features]]. In general, the support is below:

<table>
  <tr><th>Browser</th><th>Supported</th><th>Automated Testing</th><th>Notes</th></tr>
  <tr>
    <td>Firefox Stable</td>
    <td>yes</td>
    <td>Windows and Linux</td>
    <td></td>
  </tr>
  <tr>
    <td>Chrome Stable</td>
    <td>yes</td>
    <td>Windows and Linux</td>
    <td></td>
  </tr>
  <tr>
    <td>Opera Stable</td>
    <td>yes</td>
    <td>none</td>
    <td></td>
  </tr>
  <tr>
    <td>Android</td>
    <td>limited</td>
    <td>none</td>
    <td>Android's Web Browser version 4.0 or below lacks a number of features or has defects, e.g. in typed arrays or HTTP range requests</td>
  </tr>
  <tr>
    <td>Safari</td>
    <td>limited</td>
    <td>none</td>
    <td>Safari (desktop and mobile) lacks a number of features or has defects, e.g. in typed arrays or HTTP range requests</td>
  </tr>
  <tr>
    <td>IE9</td>
    <td>limited</td>
    <td>none</td>
    <td>IE9 lacks a number of features and most notably typed arrays which causes subpar performance.</td>
  </tr>
  <tr>
    <td>&lt;=IE8</td>
    <td>NO</td>
    <td>none</td>
    <td>IE8 and below are missing too many features to be supported.</td>
  </tr>
</table>

<a name="faq-extensions"></a>
## What browsers have extensions (and where can I find install procedures)?
There is currently a Firefox, Chromium and Opera extension.  The Firefox extension is well supported and actively worked on. The Chromium extension is maintained by a PDF.js contributor. The Opera extension can be found [here](https://addons.opera.com/extensions/details/pdf-viewer). For installing the Firefox or Chromium extension, please refer to the [readme](https://github.com/mozilla/pdf.js/blob/master/README.md).

<a name="faq-contrib"></a>
## I know JavaScript and want to contribute to the project. How do I start?
First, you need to prepare your [fork](https://help.github.com/articles/fork-a-repo) and setup the development environment. Don't forget to read the [[Contributing]] page. Second, make yourself familiar with the [PDF format and PDF.js internals](Additional-Learning-Resources). Third, if you don't already have a certain issue you want to fix, choose one from the [open issues labeled 5-good-beginner-bug](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open).  Last, submit a [pull request](https://help.github.com/articles/using-pull-requests) for the review. _During any part of the process we recommend to communicate with the PDF.js team on #pdfjs IRC channel at irc.mozilla.org if you have questions or need to find a reviewer._

<a name="faq-annotations"></a>
## Is it possible to add annotations to a PDF?
PDF.js is mainly written for *reading* PDF files, not editing them. Because of that we don't yet support adding any kind of annotations. We do however support rendering a number of annotation types for viewing.

<a name="faq-shortcuts"></a>
## What are the PDF.js keyboard shortcuts?
(warning, the following list may be incomplete)

### Navigation
* **next page:** <kbd>n</kbd>, <kbd>k</kbd>, right arrow key, click in presentation mode
* **previous page:** <kbd>p</kbd>, <kbd>j</kbd>, left arrow key, <kbd>Shift</kbd> + click in presentation mode

The <kbd>home</kbd>, <kbd>end</kbd>, <kbd>page up</kbd>, <kbd>page down</kbd> and all arrow keys can be used to navigate the document.

### Viewer controls
User interface buttons or <kbd>ctrl</kbd> + mouse wheel can be used to change the zooming level, but keyboard shortcuts are also available:
* **zoom in:** <kbd>ctrl</kbd> + <kbd>+</kbd>, <kbd>ctrl</kbd> + <kbd>=</kbd>
* **zoom out:** <kbd>ctrl</kbd> + <kbd>-</kbd>
* **restore normal zoom:** <kbd>ctrl</kbd> + <kbd>0</kbd>
* **rotate the document clockwise:** <kbd>r</kbd>
* **rotate counterclockwise:** <kbd>shift</kbd> + <kbd>r</kbd>
* **presentation mode:** <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>p</kbd>
* **toggle hand tool:** <kbd>h</kbd>
* **move focus to the 'go to page' box:** <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>g</kbd>

(replace ctrl with meta on some configurations)

<a name="minified"></a>
## PDF.js files are too big. Can you provide minified versions of CSS and JS files?

Not at the moment. The PDF.js is not automatically tested with any of minifiers. We are keeping it up to the website administrators to choose which minifier they want to use.

It is known that minifiers break PDF.js code if advanced options are used (see [#710](https://github.com/mozilla/pdf.js/issues/710) or [#2479](https://github.com/mozilla/pdf.js/issues/2479)). It's safe to use minifiers in whitespace/comments-removal mode.

<a name="gh-pages"></a>
## Is there a pre-built version PDF.js available?

Yes. The code for the website at http://mozilla.github.com/pdf.js is located in the "gh-pages" branch. You can clone it using `git clone -b gh-pages https://github.com/mozilla/pdf.js.git pdfjs-gh-pages` or download [the archive](https://github.com/mozilla/pdf.js/archive/gh-pages.zip).

<a name="issue"></a>
## PDF.js does not render my files correctly. Can I report an issue?

Yes. The issues are used to track both bugs filed by users and specific work items for developers. Try to file one issue per problem observed.

Please specify valid title (e.g. "Glyph spacing is incorrect" instead of "PDF.js does not work") and provide more details about the issue: link to the PDF, location in the PDF, screenshot, browser version, operating system, PDF.js version and JavaScript console warning/error messages. The issues that do not have enough details provided will be closed as invalid/incomplete.

<a name="corrupted-pdf"></a>
## I know that my PDFs are corrupted. Will PDF.js attempt to display it?

Yes. PDF.js will attempt to recover usable PDF data (pages, content or fonts) and display the document. Please report the issue (see above) and we will take a look.

<a name="idea"></a>
## I have a really great idea. Where is the best place to record it?

The best place is our dev-pdf-js@lists.mozilla.org mailing list. You can subscribe to it using [lists.mozilla.org](https://lists.mozilla.org/listinfo/dev-pdf-js) or [Google Groups](https://groups.google.com/group/mozilla.dev.pdf-js/topics). This way you will reach not only developers. As an alternative, you can join our [weekly engineering meeting](https://github.com/mozilla/pdf.js/wiki/Weekly-Public-Meetings) to discuss new ideas for the project.

The issue tracking system is designed to record a single technical problem. A bug report is something where a developer/contributor can work on. The [GitHub issue tracker](https://github.com/mozilla/pdf.js/issues?state=open) is not a good place for general, not well thought out or unworkable ideas. Most likely a discussion-type issue will not be addressed for a long time or closed as invalid.

<a name="custom"></a>
## I'm developing a custom solution based on PDF.js core library. Can you help me?

We are glad to hear that and will try to help you, but first check examples at https://github.com/mozilla/pdf.js#learning and search existing [issues](https://github.com/mozilla/pdf.js/search?q=keyword&type=Issues). If this does not help, please prepare short well-documented example that demonstrate the problem and make it accessible online on your website, jsbin, etc. before opening a new issue or contacting us on the IRC channel -- keep in mind that just code snippets won't help us troubleshoot the problem. The issues that do not provide enough details will be closed as invalid/incomplete (see [reporting issue](#issue) above).

Please periodically check or subscribe to our dev-pdf-js@lists.mozilla.org mailing list to be informed about changes in the PDF.js architecture/design or security announcements.