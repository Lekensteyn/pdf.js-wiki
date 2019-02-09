1. `git fetch upstream`
1. `git checkout upstream/master`
1. Create the ZIP file: `gulp publish`
1. Create the release on GitHub:
    1. Navigate to https://github.com/mozilla/pdf.js/releases/new
    1. Call the release and tag `v{version}` and insert the version from the name of the ZIP file.
    1. Attach the ZIP file from the step above and include release notes
        1. Clone https://github.com/brendandahl/pdf.js.utils
        2. Run `python2 release.py {last_pr_number}`, where `{last_pr_number}` is the last PR number (without hash) in the release notes of the existing release
    1. Check the box for this release being a pre-release!
    1. Label the existing release as stable
1. Update `pdfjs.config` to bump both the stable and beta version numbers:
    1. Bump the major/minor version number of the `versionPrefix`
    1. Bump the stable/beta version number
    1. Set `baseVersion` to the commit ID of the merge commit
1. Eat cake, a cookie or any other treat