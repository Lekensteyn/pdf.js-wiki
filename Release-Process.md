The objective is to release a version every six weeks. Ideally this should be one week before Firefox uplift dates; see https://wiki.mozilla.org/RapidRelease/Calendar.

### After an `api-(minor|major)` pull request is merged:

Update the `pdfjs.config` file:

1. Bump the major/minor version number of the `versionPrefix`.
1. Set `baseVersion` to the commit ID of the merged commit.

### Releasing a new version

1. `git fetch upstream`
1. `git checkout upstream/master`
1. Run `gulp publish` to generate the zip
1. Create github release
    1. add release notes
    1. attach zip generated from above
    1. mark as pre-release
1. Remove pre-release flag from previous beta release
1. Eat cake, cookie or any other treat