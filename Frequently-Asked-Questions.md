* [Can I specify different PDF in the default viewer?](#file)
* [Can I load a PDF from another server (cross domain request)?](#faq-xhr)
* [What browsers are supported?](#faq-support)
* [What browsers have extensions (and where can I find install procedures)?](#faq-extensions)
* [I know JavaScript and want to contribute to the project. How do I start?](#faq-contrib)
* [Is it possible to add annotations to a PDF?](#faq-annotations)

<a name="file"></a>
## Can I specify different PDF in the default viewer?
You can modify DEFAULT_URL variable in the web/viewer.js file. Or, you can append the `?file=` query string to the viewer URL, e.g. `http://mozilla.github.com/pdf.js/web/viewer.html?file=compressed.tracemonkey-pldi-09.pdf`.

<a name="faq-xhr"></a>
## Can I load a PDF from another server (cross domain request)?
Not by default, but it is possible.  PDF.js runs with the same permissions as any other javascript, which means it cannot do cross origin requests (see [Same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy) and [example](https://gist.github.com/3452072)).  There are some possible ways to get around this such as using [CORS](http://enable-cors.org/) or setting up a proxy on your server that will feed pdf.js the pdf.  Both workarounds are out of the scope of the pdf.js project and we will not provide code to do either.

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
## What browsers have extensions(and where can I find install procedures)?
There is currently a Firefox and Chrome extension.  The Firefox extension is well supported and actively worked on.  The Chrome extension is less active and more experimental. For installing either see the [readme](https://github.com/mozilla/pdf.js/blob/master/README.md).

<a name="faq-contrib"></a>
## I know JavaScript and want to contribute to the project. How do I start?
First, you need to prepare your [fork](https://help.github.com/articles/fork-a-repo) and setup the development environment. Don't forget to read the [[Contributing]] page. Second, make yourself familiar with the [PDF format and PDF.js internals](Additional-Learning-Resources). Third, if you don't already have a certain issue you want to fix, choose one from the [open issues labeled 5-good-beginner-bug](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open).  Last, submit a [pull request](https://help.github.com/articles/using-pull-requests) for the review. _During any part of the process we recommend to communicate with the PDF.js team on #pdfjs IRC channel at irc.mozilla.org if you have questions or need to find a reviewer._

<a name="faq-annotations"></a>
## Is it possible to add annotations to a PDF?
PDF.js is mainly written for *reading* PDF files, not editing them. Because of that we don't yet support adding any kind of annotations. We do however support rendering a number of annotation types.