The objective is to release a version every six weeks. Ideally this should be one week before Firefox uplift dates; see https://wiki.mozilla.org/RapidRelease/Calendar.

### After an `api-(minor|major)` pull request is merged:

Update the `pdfjs.config` file:

1. Bump the major/minor version number of the `versionPrefix`.
1. Set `baseVersion` to the commit ID of the merged commit.

### Releasing a new version

1. `git fetch upstream`
1. `git checkout upstream/master`
1. Create the ZIP file: `gulp publish`
1. Create the release on GitHub:
    1. Navigate to https://github.com/mozilla/pdf.js/releases/new
    1. Call the release and tag `v{version}` and insert the version from the name of the ZIP file.
    1. Attach the ZIP file from the step above and include release notes
        1. Clone https://github.com/brendandahl/pdf.js.utils
        2. Run `release.py`
    1. Label the existing release as stable
    1. Label the new release as pre-release
1. Update `pdfjs.config` to bump both the stable and beta version numbers
1. Eat cake, a cookie or any other treat