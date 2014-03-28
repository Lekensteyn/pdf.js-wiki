If you are not familiar with PDF.js, then first take a look at the README's getting started section.

## Contributing Code
An overview how to contribute code to the PDF.js project. The basic workflow:

1. Fork
1. Feature branch
1. Make changes
1. Run lint and testing
1. Push changes to your fork/branch
1. Create pull request
1. Code review and automated testing
1. Merge into master

### The Bare Necessities
* Git client
* GitHub account
* [Node.js](http://nodejs.org/)
* (for Windows, see [[Setting up pdf.js Development Environment for Windows]])
* (for font or performance testing you will need [python](http://www.python.org/download/), included with mozilla-build for Windows)

**Before you make any changes to the code you'll probably want jump down to [Generating Reference Images](#ref-images) to create the reference snapshot images so you can run the test framework and check for regressions.**
 
If you're familiar with GitHub and creating feature branches you can skip down to [Run Lint and Testing](#lint)...

### 1) Fork
To fork the repository you'll need to sign up for a GitHub account. Once you have an account just click the little fork button up top. Now that you have your fork you'll need to clone it (replace `<YOUR USERNAME>`):
```
git clone git://github.com/<YOUR USERNAME>/pdf.js.git
```

It's useful to have the upstream repository registered as well
```
git remote add upstream git://github.com/mozilla/pdf.js.git
```
and periodically fetch it using `git fetch upstream`.

### 2) Branch
We try to do everything in feature branches. For example, to create and switch to a type 3 font branch use:
```
git checkout -b type3fontsupport upstream/master
```

### 3) Changes
Now that you have new branch created you can edit/add/delete files. Follow the standard Git workflow to stage and locally commit your changes -- there are lots of guides that explain Git.

If the branch contains lot of small commits, you might be asked to squash the commits. You can use Git's rebase option or follow the [[Squashing Commits]] instructions.

### <a id="lint"></a> 4) Run Lint and Testing
**Run Lint**

Make sure your code follows our style guides and run from the PDF.js folder:

```
node make lint
```
The first time you run the command above, jshint will be automatically installed in the PDF.js folder.

***Protip***: If you are a Vim user, then install [syntastic](http://www.vim.org/scripts/script.php?script_id=2736) and add the following line to your `.vimrc`:

```
let g:syntastic_javascript_checker = "jshint"
```

Now you have automatic linting of your changes to JavaScript files whenever you save.

**Run Testing**

To ensure your changes didn't introduce any regressions you need to run the testing framework. There are four basic types of tests:

* load - just checks if the PDF file can be loaded without crashing
* eq - a reference test which takes correctly rendered snapshots and compares them to the snapshots created by the current code
* fbf - a forward back forward test
* unit tests - Jasmine unit tests that are run separately from the above tests

<a id="ref-images"></a>**Generating Reference Images**

The reference tests require you to generate the original snapshots for comparison. The snapshots should be generated before you make any changes. If you have already made some changes, `git stash` your work. Then make sure you have setup a `browser_manifest` file. There are templates located in `test/resources/browser_manifests/`.  Copy one of the templates (replace `<your os>` with Mac, Linux or Windows).

```
cp test/resources/browser_manifests/browser_manifest.json.<your os> test/resources/browser_manifests/browser_manifest.json
```
Then edit the manifest in your favorite editor and make sure it points to the browser(s) you want to use for generating the reference images.

Now we can generate the reference images:

```
cd test/
node test.js -m --browserManifestFile=resources/browser_manifests/browser_manifest.json
```
You can then run the test suite from the PDF.js root folder:

```
node make test
```

**Running Unit Tests Separately**

Unit tests are run when `node make test` is run, but they can also be run separately two different ways:

1. In browser - A web server has to be setup to host the PDF.js files. Tests will be executed by opening the _\<url-to-pdf.js\>_/test/unit/unit_test.html page. If the web server is created by using `node make server` command, the URL will be http://localhost:8888/test/unit/unit_test.html.
2. Command Line - `node make unittest` which will run all the test using the regression test framework.

### 5) Push Changes
After lint and all tests pass, push the changes to your fork/branch on GitHub:
```
git push origin type3fontsupport
```

### 6) Pull Request
Create a pull request on GitHub for your feature branch. The code will then be reviewed and tested further by our bot.

Note that the translations for PDF.js in the `l10n` folder are synchronized with the Aurora branch of Mozilla Firefox. This means that we will only accept pull requests that add strings currently missing in the Aurora branch (because it will take at least six weeks before the most recent translations are in the Aurora branch), but keep in mind that the changes will be overwritten when we synchronize again.

### 7) Code Review and Further Testing
In addition to the GitHub pull request workflow, it's highly recommended that you setup some form of communication with the PDF.js team via the #pdfjs IRC channel at irc.mozilla.org or e-mail. That will help to find a reviewer for your patch and speed up the review process.

A collaborator will kick off further testing and do a code review.

Something to speed up fetching the branch for the remote github repo using `git try username:branch` command -- add the following to the '.git/config':
```
[alias]
  try = !sh -c 'IFS=\":\" read -ra ARGS <<< \"$0\" && git fetch https://github.com/${ARGS[0]}/pdf.js.git ${ARGS[1]} && git checkout FETCH_HEAD'
```

### 8) Merging to master
If all goes well, a collaborator will merge all your changes into the main repository.

## Useful artifacts

* File split (issues #700 and #646)
* API (issue #1100 and [api.js](https://github.com/mozilla/pdf.js/blob/master/src/display/api.js))