## URL Parameters
pdf.js has several special url parameters to alter how pdf.js works and enable debugging tools.  All of these parameters go into the hash section of the url (after the # symbol) and follow a query string syntax (e.g. #param1=value1&param2=value2). Note: since all of these parameters are in the hash section you have to refresh the page after adding them.

* `pdfBug=all` - Enables all the debugging tools.  You can optionally enable specific tools by specifying them by their id e.g. pdfBug=FontInspector or pdfBug=Stepper,FontInspector. More about PDFBug below.
* `disableWorker=true` - Disables the worker which makes it easier to use debugging tools like firebug where workers aren't supported yet.
* `disableTextLayer=true` - Disables the text layer that is used for text selection.

## PDFBug Tools
To enable see above.
### Font Inspector
`id: FontInspector`

The font inspector allows you to view what fonts are used within page.  It also allows you to download the base64 version of the font which can be copied into the online font sanitizer that provides more information about why a font is being rejected (see http://async5.org/ots/ots.html). Further, you can download the font and use the base64 command on most unix systems to decode the font and save it as a true type font file.  The decoded font file can then be checked with more programs such as [FontForge](http://fontforge.sourceforge.net/) or on windows [Microsoft Font Validator](http://www.microsoft.com/typography/FontValidator.mspx)

### Stepper
`id: Stepper`

The stepper tool makes it so you can step through the drawing commands one at a time and hopefully find where a possible issue is coming from. It is also useful for learning how a PDF is structured and the order of its operations.  To walk through the drawing commands first add a break point, refresh the page and then use the keys `s` to step one command at a time or `c` to continue until the next breakpoint(line that is checked).