* [Can I load a pdf from another server (cross domain request)?](#faq-xhr)
* [What browsers are supported (and where can I find install procedures)?](#faq-yis)
* [I know JavaScript and want to contribute to the project. How do I start?](#faq-contrib)


<a name="faq-xhr"></a>
## Can I load a pdf from another server (cross domain request)?
Not by default, but it is possible.  Pdf.js runs with the same permissions as any other javascript, which means it cannot do cross origin requests (see [Same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy) and [example](https://gist.github.com/3452072)).  There are some possible ways to get around this such as using [CORS](http://enable-cors.org/) or setting up a proxy on your server that will feed pdf.js the pdf.  Both workarounds are out of the scope of the pdf.js project and we will not provide code to do either.

<a name="faq-yis"></a>
## What browsers are supported (and where can I find install procedures)?
FireFox is widely supported and installation procedures are described in the README.md at the PDF.js GitHub landing page [https://github.com/mozilla/pdf.js]. 

<a name="faq-contrib"></a>
## I know JavaScript and want to contribute to the project. How do I start?
First, you need to prepare your [fork](https://help.github.com/articles/fork-a-repo) and setup the development environment. Don't forget to read the [[Contributing]] page. Second, make yourself familiar with the [PDF format and PDF.js internals](Additional-Learning-Resources). Third, if you don't already have a certain issue you want to fix, choose one from the [open issues labeled 5-good-beginner-bug](https://github.com/mozilla/pdf.js/issues?direction=desc&labels=5-good-beginner-bug&page=1&sort=created&state=open).  Last, submit a [pull request](https://help.github.com/articles/using-pull-requests) for the review. _During any part of the process we recommend to communicate with the PDF.js team on #pdfjs IRC channel at irc.mozilla.org if you have questions or need to find a reviewer._
