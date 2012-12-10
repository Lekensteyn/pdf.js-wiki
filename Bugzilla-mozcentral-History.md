

## 0.6.172
https://bugzilla.mozilla.org/show_bug.cgi?id=817924

* #2394 Change keys for find wrapped strings.
* #2397 Update the keys to match recent changes
* #2402 Update l10n/ja/viewer.properties
* #2400 combineUrl fix
* #2405 Update src/obj.js
* #2413 Bug 815475 - Fix pdfjs when there is no integrated findbar (pdfjs 0.6.39 ...
* #2415 Add close button and title bar for b2g.
* #2406 Fixes function array support for radial/axial pattern
* #2346 Adds basic PDF info
* #2369 Updates webL10n; using viewer.properties as is...
* #2420 New GUI for B2g.
* #2418 Initial refactoring to reduce amount of getRgb calls and objects creation
* #2423 Refactors Lab CS; uses different conversion for D50 and D65
* #2426 Fixes "TypeError: info is undefined"
* #2427 pdf.js features testing

## 0.6.123
https://bugzilla.mozilla.org/show_bug.cgi?id=810107

* #2265 Fixes test pdfs MD5; make server does not download
* #2272 add uppercase extension recognition for Chrome
* #2270 Using CMYK SWOP colors
* #2285 Allow find to highlight matches without extracting all text.
* #2249 Reducing parameter of Mac->Win heuristic
* #2292 Implement NullStream, fixes #1832
* #2293 Fix annotation clipping
* #2283 Fixes output for HiDPI device
* #2299 Cleared some unused code
* #2295 Make comments look nicer
* #2303 Fixes getNumber at the end of stream
* #2305 Remove use of innerhtml.
* #2309 Forward original request to avoid firefox assertion.
* #2298 Display an error on Invalid PDF
* #2311 Change the channel owner to the resource url.
* #2315 Add more annotation icons
* #2319 Update l10n/ja/viewer.properties
* #2318 try/catch fallback fails to disable linearization
* #2322 Update zh-TW translation
* #2317 Refactors how page objects are stored
* #2323 Vectorize the logo
* #2326 Fixes Util is not defined in acroforms example when running in prod mode
* #2313 Fixes incomplete restore in paintFormXObject
* #2328 Minor css tweaks for small viewer and aligning borders.
* #2330 Fix typo in PartialEvaluator_getTextContent
* #2327 Un-inline pdf.js for the extension/mozcentral and remove fetch pdf by content code.
* #2335 Fix cllosure compiler warning for uninitialized variables
* #2339 Fix the initialization of the first page for multiple testing rounds.
* #2340 Fixes lineWidth/scale calculation for the fonts
* #2341 Fixes stream loading for XRefStm
* #2312 Test harness for fonts (uses ttx)
* #2345 Revisiting the Chrome URL patch, #1969
* #2347 Fixing Chromium regression
* #2343 Fixes compressed object entries caching
* #2342 Add mozcentraldiff target
* #2246 Re-creates invalid post table
* #2248 Verifies some of the OS2 font table fields
* #2350 Add license headers to properties files.
* #2363 Fix bugzilla bug#804526, hiding fullscreen button when in an iframe
* #2360 Refactor constant names in various files
* #2356 Update fr locale from mozilla-central
* #2365 Add license header to the rest of the l10n properties files

## 0.6.39
https://bugzilla.mozilla.org/show_bug.cgi?id=801280
* #2169 Update zh-TW Translation
* #2173 Fixes function declaration for strict mode
* #2167 Tune whitespace insertion
* #2180 Prevents key handling when the input/toolbar controls are focused
* #2182 Removed en-US from link to stable version in Readme
* #2179 Fixes private browsing history
* #2186 Bug 796584 - Don't use localStorage in pdf.js
* #2193 Change how we get the resource principal.
* #2195 Removes usage of print as log
* #2168 Find bar
* #2192 Fix the first run code and make it possible to run multiple times.
* #2196 Fixes console log methods for IE9
* #2199 Minor CSS fixed for find bar
* #2200 Update zh-TW find panel translation
* #2198 Bug 792582 - Explicitly set privacy status of channels created by pdf.js
* #2197 Add support for firefox integrated find.
* #2202 Fixes minor find bugs.
* #2205 Handle ctrl/cmd+g for html findbar.
* #2060 Add firefox mouse scrolling support in fullscreen mode.
* #2208 Add pilot find next/prev icons; localization
* #2211 Escape key closes findbar
* #2220 Fixes font debugger; text builder api refactoring
* #2223 Fixes order in which divs are added to the text layer
* #2224 Fixes Viewport rotation above 360
* #2210 Adds more presentation mode controls
* #2206 Converted the first and last page buttons to context menu items
* #2225 Renewed the Dutch translations and added all missing strings
* #2226 Improved the Dutch and English strings for the first and last page context menu items
* #2227 Delay extracting text until first find event.
* #2228 Rounding page div width and height...
* #2217 Hides cursor in presentation mode
* #2231 Only use the integrated find if we aren't in an frame.
* #2238 Bump the version number to 0.6.
* #2241 Update l10n/ja/viewer.properties
* #2252 Removes 'visiblePages[0] is undefined' error
* #2239 Stops font processing when valid glyphs are absent in the font
* #2213 Removes PutBinaryImageData compatibility check (re:bug 762657)
* #2254 Fixes font processing when no glyphs are found
* #2233 Fixes fit-page and fullscreen
* #2214 Adds Type1 sbw command support for horizontal fonts
* #2215 Falls back to ErrorFont when font object is not available or corrupted
* #2256 Increase wait timeout for api unit tests.
* #2257 More descriptive link types warning
* #2240 Fixes text clipping
* #2258 Addresses review feedback from mc bug 801280.
* #2244 Fixes cmap when 0xFFFF character is included
* #2243 Removes useless font tables for PDF rendering
* #2262 Support 'GoToR'-type links
* #2245 Fixes reading CFF with two .notdef in charset

