Overview: Release a version every six weeks.  Ideally this should be one week before Firefox uplift dates, see https://wiki.mozilla.org/RapidRelease/Calendar

1. [Update pdf.js on mozilla central.](https://github.com/mozilla/pdf.js/wiki/Updating-pdf.js-on-Mozilla-Central)
1. Get review. If there's feedback, fix it and return to step 1.
1. Update the AMO addon with the final reviewed version from above.
1. Create a tag and push it github.
```
git tag v0.4.11 -m "v0.4.11 Firefox 17"
git push upstream v0.4.11
```
