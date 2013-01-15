If you're not familiar with pdf.js first see the readme getting started section.

## Contributing Code
An overview how to contribute code to the pdf.js project.  The basic workflow:

1. fork
1. feature branch
1. make changes
1. run lint and testing
1. push changes to your fork/branch
1. create pull request
1. code review & automated testing
1. merge into the master

### The Bare Necessities
* git client
* github account
* [python](http://www.python.org/download/)
* [node](http://nodejs.org/)
* [gjslint](https://developers.google.com/closure/utilities/docs/linter_howto) - _Use version 2.3.5_ 
    * [easy_install on Ubuntu](http://www.hacksparrow.com/ubuntu-how-to-install-easy_install.html)
* (for Windows, see [[Setting up pdf.js Development Environment for Windows]])

**Before you make any changes to the code you'll probably want jump down to [Generating Reference Images](#ref-images) to create the reference snapshot images so you can run the test framework and check for regressions.**
 
If you're familiar with github and doing feature branches you can skip down to [Run Lint and Testing](#lint)...

### 1) Fork
To fork the repository you'll need to sign up for a github account. Once you have an account just click the little fork button up top. Now that you have your fork you'll need to clone it (replace `<YOUR USERNAME>`):
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
Now that you have new branch created you can edit/add/delete files. Follow the standard git workflow to stage and locally commit your changes -- there are lots of guides that explain git.

If the branch contains lot of small commits, you might be asked to squash the commits. You can use git rebase option or follow the [[Squashing Commits]] instructions.

### <a id="lint"></a> 4) Run Lint and Testing
**Run Lint**

Make sure your code follows our style guides, run from the pdf.js folder:

```
node make lint
```

***Protip***: If you are a Vim user, then install [syntastic](http://www.vim.org/scripts/script.php?script_id=2736) and add the following line to your `.vimrc`:

```
let g:syntastic_javascript_checker = "gjslint"
```

Now you have automatic linting of your changes to javascript files whenever you save.

**Run Testing**

To ensure your changes didn't introduce any regressions you'll need to run the testing framework. There are four basic types of tests:

* load - just checks if the pdf file can be loaded without crashing
* eq - a reference test which takes correctly rendered snapshots and compares them to the snapshots created by the current code
* fbf - a forward back forward test
* unit tests - jasmine unit tests that are run separately from the above tests

<a id="ref-images"></a>**Generating Reference Images**

The reference tests require you to generate the original snapshots for comparison.  The snapshots should be generated before you make any changes. If you have already made some changes `git stash` your work. Then make sure you have setup a browser_manifest file.  There are templates located in `test/resources/browser_manifests/`.  Copy one of the templates (replace `<your os>` with mac, linux, or win).

```
cp test/resources/browser_manifests/browser_manifest.json.<your os> test/resources/browser_manifests/browser_manifest.json
```
Then edit the manifest in your favorite editor and make sure it points to the browser(s) you want to use for generating the reference images.

Now we can generate the reference images:

```
cd test/
python test.py -m --browserManifestFile=resources/browser_manifests/browser_manifest.json
```
You can then run the test suite from the pdf.js root folder:

```
node make test
```

**Running Unit Tests Separately**

Unit tests are run when `node make test` is run but they can also be run separately two different ways:

1. In browser - A web server has to be setup to host the pdf.js files. Tests will be executed by opening the _\<url-to-pdf.js\>_/test/unit/unit_test.html page. If the web server is created by using `node make server` command, the URL will be http://localhost:8888/test/unit/unit_test.html.
2. Command Line - `node make unittest` which will run all the test using the regression test framework.

### 5) Push Changes
After lint and all tests pass, push changes to your fork/branch on github:
```
git push origin type3fontsupport
```

### 6) Pull Request
Create a pull request on github for your feature branch. The code will then be reviewed and tested further by our pdfbot.

### 7) Code Review & Further Testing
In addition to the github pull request workflow, it's highly recommended that you setup some form of communication with pdf.js team via #pdfjs IRC channel at irc.mozilla.org or e-mail. That will help to find a reviewer for your patch and speed up the review process.

A collaborator will kick off further testing and do a code review.

### 8) Merging to Master
If all goes well a collaborator will merge all your changes into the main repo.

## Useful artifacts

* File split (issues #700 and #646)
* API (issue #1100 and [api.js](https://github.com/mozilla/pdf.js/blob/master/src/api.js))