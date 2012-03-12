* [Can I load a pdf from another server (cross domain request)?](#faq-xhr)

<a name="faq-xhr"></a>
## Can I load a pdf from another server (cross domain request)?
Not by default, but it is possible.  Pdf.js runs with the same permissions as any other javascript, which means it cannot do cross origin requests (see [Same origin policy](http://en.wikipedia.org/wiki/Same_origin_policy)).  There are some possible ways to get around this such as using [CORS](http://enable-cors.org/) or setting up a proxy on your server that will feed pdf.js the pdf.  Both workarounds are out of the scope of the pdf.js project and we will not provide code to do either.