Overview: Release a version every six weeks.  Ideally this should be one week before Firefox uplift dates, see https://wiki.mozilla.org/RapidRelease/Calendar

1. [Update pdf.js on mozilla central.](https://github.com/mozilla/pdf.js/wiki/Updating-pdf.js-on-Mozilla-Central)
1. `git checkout <SHA IN MOZ CENTRAL>`
1. Run `node make publish` to generate the zip and update pdfjs.confg
1. Create a PR with pdfjs.config changes
1. Create github release
   2. add release notes
   2. attach zip generated from above
   2. mark as pre-release
1. Remove pre-release flag from previous beta release
1. Eat cake
