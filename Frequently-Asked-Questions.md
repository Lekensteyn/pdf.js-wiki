* [Can I specify different PDF in the default viewer?](#file)
* [Can I load a PDF from another server (cross domain request)?](#faq-xhr)
* [What browsers are supported?](#faq-support)
* [What browsers have extensions (and where can I find install procedures)?](#faq-extensions)
* [I know JavaScript and want to contribute to the project. How do I start?](#faq-contrib)
* [Is it possible to add annotations to a PDF?](#faq-annotations)
* [What are the PDF.js keyboard shortcuts?](#faq-shortcuts)
* [PDF.js files are too big. Can you provide minified versions of CSS and JS files?](#minified)
* [Is there a pre-built version PDF.js available?](#gh-pages)

<a name="file"></a>
## Can I specify different PDF in the default viewer?
You can the modify `DEFAULT_URL` variable in the web/viewer.js file. Or, you can append the `?file=` query string to the viewer URL, e.g. `http://mozilla.github.com/pdf.js/web/viewer.html?file=compressed.tracemonkey-pldi-09.pdf`.

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
There is currently a Firefox, Chrome and Opera extension.  The Firefox extension is well supported and actively worked on. The Chrome extension is maintained by a PDF.js contributor. The Opera extension can be found [here](https://addons.opera.com/extensions/details/pdf-viewer). For installing the Firefox or Chrome extension, please refer to the [readme](https://github.com/mozilla/pdf.js/blob/master/README.md).

<a name="faq-contrib"></a>
## I know JavaScript and want to contribute to the project. How do I start?
First, you need to prepare your [fork](https://help.github.com/articles/fork-a-repo) and setup the development environment. Don't forget to read the [[Contributing]] page. Second, make yourself familiar with the [PDF format and PDF.js internals](Additional-Learning-Resources). Third, if you don't already have a certain issue you want to fix, choose one from the [open issues labeled 5-good-beginner-bug](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open).  Last, submit a [pull request](https://help.github.com/articles/using-pull-requests) for the review. _During any part of the process we recommend to communicate with the PDF.js team on #pdfjs IRC channel at irc.mozilla.org if you have questions or need to find a reviewer._

<a name="faq-annotations"></a>
## Is it possible to add annotations to a PDF?
PDF.js is mainly written for *reading* PDF files, not editing them. Because of that we don't yet support adding any kind of annotations. We do however support rendering a number of annotation types.

<a name="faq-shortcuts"></a>
## What are the PDF.js keyboard shortcuts?
(warning, the following list may be incomplete)
### Navigation
* **next page:** n, k, right arrow key
* **previous page:** p, j, left arrow key

In full screen mode, the home, end, page up, page down, and all arrow keys can be used to navigate the document.
### Zoom and rotate
User interface buttons or ctrl + mouse wheel can be used to change the zooming level, but keyboard shortcuts are also available:
* **zoom in:** ctrl + "+", ctrl + = 
* **zoom out:** ctrl + -
* **restore normal zoom:** ctrl + 0 (in full screen mode)
* **rotate the document clockwise:** r
* **rotate counterclockwise:** shift + r
* **presentation mode:** ctrl + alt + p

(replace ctrl with meta on some configurations)

<a name="minified"></a>
## PDF.js files are too big. Can you provide minified versions of CSS and JS files?

Not at the moment. The PDF.js is not automatically tested with any of minifiers. We are keeping it up to the web site administrators to choose which minifier they want to use.

It is known that minifiers break PDF.js code if advanced options are used (see [#710](https://github.com/mozilla/pdf.js/issues/710) or [#2479](https://github.com/mozilla/pdf.js/issues/2479)). It's safe to use minifiers in whitespace/comments-removal mode.

<a name="gh-pages"></a>
## Is there a pre-built version PDF.js available?

Yes. The code for the web site at http://mozilla.github.com/pdf.js is located in the "gh-pages" branch. You can clone it using `git clone -b gh-pages https://github.com/mozilla/pdf.js.git pdfjs-gh-pages`
