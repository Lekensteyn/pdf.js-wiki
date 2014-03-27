## Enabling
As a safety precaution the debugging tools for the extension and the version of PDF.js bundled with Firefox will require the user to set/create a boolean preference in `about:config`:

* Extension version: `extensions.uriloader@pdf.js.pdfBugEnabled` setting (boolean `true`)
* Mozilla Central (Firefox) version: `pdfjs.pdfBugEnabled` setting (boolean `true`)

## URL Parameters
PDF.js has several special URL parameters to alter how PDF.js works and to enable debugging tools. All of these parameters go into the hash section of the URL (after the # symbol) and follow a query string syntax (e.g. #param1=value1&param2=value2). Note: since all of these parameters are in the hash section, you have to refresh the page after adding them.

* `pdfBug=all` - Enables all the debugging tools. You can optionally enable specific tools by specifying them by their ID, e.g. pdfBug=FontInspector or pdfBug=Stepper,FontInspector. More about PDFBug below.
* `disableWorker=true` - Disables the worker which makes it easier to use debugging tools like Firebug where workers aren't supported yet.
* `textLayer=[off|visible|shadow|hover]` - Disables or reveals the text layer that is used for text selection.
* `disableFontFace=true` - Disables standard `@font-face` font loading and uses the internal font renderer instead.
* `disableRange=true` - Disables HTTP range requests when fetching the document.
* `disableAutoFetch=true` - Disables auto fetching of the document; only gets necessary data to display the current view.

## PDFBug Tools
See the instructions above on how to enable these tools.

### Font Inspector
`id: FontInspector`

The font inspector allows you to view what fonts are used within page. It also allows you to download the font using `Save Link As...` and naming it with a `.otf` extension. See the section below on debugging fonts.

### Stepper
`id: Stepper`

The stepper tool makes it easy for you to step through the drawing commands one at a time and hopefully find where a possible issue is coming from. It is also useful for learning how a PDF document is structured and the order of its operations. To walk through the drawing commands you must add a break point, refresh the page and then use the keys `s` to step one command at a time or `c` to continue until the next breakpoint (line that is checked).

## PDF Object Browser
Inspect the internal object structure and view raw values of a PDF document using http://brendandahl.github.io/pdf.js.utils/browser.

## Debugging Font Issues
To get a problematic font out of a PDF document, download it first using the font inspector mentioned above.

### Fonts Failing Sanitizer
If the font is failing the open type sanitizer (OTS), Firefox should show a message in the console about the rejected font. Take the base64 version of the font and paste it into the online font sanitizer that provides more information about why the font is being rejected (see http://async5.org/ots-95/ots.html).  You can then look the OTS source code linked there to find further information. 

### Helpful Font Tools
If the font isn't failing the sanitizer or the sanitizer error doesn't lead you to the font issue, it is often helpful to use other font tools to try and find the source of the problem.

**[TTX](http://sourceforge.net/projects/fonttools/)**

TTX is probably the most useful tool for debugging fonts. It provides a way to convert fonts to XML and then back to the open type format from the XML. A helpful test is to first convert the font to XML, then back to OTF and then test if the font works using a test HTML page.  

```
% ttx font.otf && ttx font.ttx
```

If the font works after running through `ttx` you can then do a binary diff of the two font files to try and track down the problematic portion. If the font still isn't working after conversion, you can then start removing parts of the XML file and converting it back to OTF to see if which section may be causing issues.

**[Adobe FDK](http://www.adobe.com/devnet/opentype/afdko.html)**

The Adobe Font Development Kit includes the above `ttx` program and several other programs such as `tx` and `sfntedit`. Running the font through `tx` can provide warnings and useful information. `tx` can be used to do a round-trip conversion to look for problems in a similar fashion as `ttx`. For example converting a CID font:

```
 % tx -t1 font.otf font.cid
 % tx -cff font.cid font.cff
 % sfntedit -a CFF=font.cff font.otf
 % sfntedit -f font.otf
```

**Other Font Tools**
* [FontForge](http://fontforge.sourceforge.net/)
* [Microsoft Font Validator](http://www.microsoft.com/typography/FontValidator.mspx)