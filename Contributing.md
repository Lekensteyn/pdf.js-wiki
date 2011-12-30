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
* git hub account
* python
* make
* jslint

Before you make any changes to the code you'll probably want jump down to the section on "Generating Reference Images" to create the reference snapshot images so you can run the test framework and check for regressions.
 
If you're familiar with github and doing feature branches you can skip down to "4) Run Lint and Testing"...

### 1) Fork
To fork the repository you'll need to sign up for a github account. Once you have an account just click the little fork button up top. Now that you have your fork you'll need to clone it (replace `<YOUR USERNAME>`):
```
git clone git://github.com/<YOUR USERNAME>/pdf.js.git
```
### 2) Branch
We try to do everything in feature branches. For example, to create and switch to a type 3 font branch use:
```
git checkout -b type3fontsupport
```
### 3) Changes
Now that you have you're branch you can edit/add/delete files.  You'll then want to stage and locally commit your changes.  I won't go into this since there are lots of guides that explain git.

### 4) Run Lint and Testing
**Run Lint**

Make sure your code follows our style guides, run from the pdf.js folder:
```
make lint
```
**Run Testing**

To ensure your changes didn't introduce any regressions you'll need to run the testing framework. There are three basic types of tests:

* load - just checks if the pdf file can be loaded without crashing
* eq - a reference test which takes correctly rendered snapshots and compares them to the snapshots created by the current code
* fbf - a forward back forward test

**Generating Reference Images**

The reference tests require you to generate the original snapshots for comparison.  The snapshots should be generated before you make any changes to the code.  If you are diligent you can just use one folder and always update the snapshots before you make code changes.  For my development, I have two pdf.js folders one that is checkout from the mozilla master and one from my own fork.  I never modify the mozilla master folder except for updating and use it to generate snapshots and then move them over to my forked pdf.js folder.  To generate these snapshots:

```
cd pdf.js/test/
python test.py -m --browserManifestFile=resources/browser_manifests/browser_manifest.json
```
That will create the references files in pdf.js/test/tmp so you'll then need to rename "tmp" to "ref" or move it to your branch and rename. Now to run the tests from the pdf.js folder:
```
make test
```

To run unit tests, the web server has to be setup to host the pdf.js files. Tests will be executed by opening the <url-to-pdf.js>/test/unit/unit_test.html page. If the web server is created by using `make server` command, the URL will be http://localhost:8888/test/unit/unit_test.html.

### 5) Push Changes
After lint and all tests pass, push changes to your fork/branch on github.

### 6) Pull Request
Create a pull request on github for your feature branch.  The code will then be reviewed and tested further by our pdfbot.

### 7) Code Review & Further Testing
A collaborator will kick off further testing and do a code review.

### 8) Merging to Master
If all goes well a collaborator will merge all your changes into the main repo.