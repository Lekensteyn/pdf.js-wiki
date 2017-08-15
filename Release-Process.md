Overview: Release a version every six weeks.  Ideally this should be one week before Firefox uplift dates, see https://wiki.mozilla.org/RapidRelease/Calendar

### After an [api-(minor|major)] Pull Request Lands:

Update pdfjs.config:

1. Bump `versionPrefix` major/minor version number
1. Set `baseVersion` to commit id of the merge commit 

### Releasing a new version

1. `git checkout upstream/master`
1. Run `gulp publish` to generate the zip
1. Create github release
   2. add release notes
   2. attach zip generated from above
   2. mark as pre-release
1. Remove pre-release flag from previous beta release
1. Eat cake, cookie or any other treat