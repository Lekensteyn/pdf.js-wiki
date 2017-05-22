If you are not familiar with PDF.js, then first take a look at the README's getting started section.

## Contributing code
Below is an overview of how to contribute code to the PDF.js project. The basic workflow is as follows:

1. Fork
1. Create feature branch
1. Make changes
1. Run lint and testing
1. Push changes to your fork/branch
1. Create pull request
1. Code review and automated testing
1. Merge into master

### Prerequisites
* Git client
* GitHub account
* [Node.js](http://nodejs.org/)
* Gulp (via `npm install -g gulp-cli`)
* An ES6 compatible browser

If you develop on Windows, read [[Setting up pdf.js Development Environment for Windows]]. For font testing you will need [Python](http://www.python.org/download).

_Before you make any changes to the code you will probably want jump down to the "Generating reference images" section to create the reference snapshot images so you can run the test framework and check for regressions._
 
If you are familiar with GitHub and creating feature branches you can skip down to the "Run lint and testing" section.

### 1. Fork
To fork the repository you need to have a GitHub account. Once you have an account you can click the fork button up top. Now that you have your fork you need to clone it (replace `{username}` with your GitHub username) using
```
git clone git://github.com/{username}/pdf.js.git
cd pdf.js
```

and pull additional libraries and tools:
```
git submodule init
git submodule update
npm install
```

It is useful to have the upstream repository registered as well using
```
git remote add upstream git://github.com/mozilla/pdf.js.git
```
and periodically fetch it using `git fetch upstream`.

### 2. Create feature branch
We always work with feature branches. For example, to create and switch to branch use:
```
git checkout -b {branch_name} upstream/master
```
and replace `{branch_name}` with a meaningful name that describes your feature or change. For instance,
if you are working on adding support for Type3 fonts, a good branch name would be `type3-font-support`.

### 3. Make changes
Now that you have a new branch you can edit/create/delete files. Follow the standard Git workflow to stage and locally commit your changes -- there are lots of guides that explain Git.

If the branch contains lot of small commits, you might be asked to squash the commits. You can use Git's rebase option or follow the instructions on the [[Squashing Commits]] page.

### 4. Run lint and testing
**Run lint**

Make sure that your code follows our [[Style Guide]] and run from the PDF.js folder:

```
gulp lint
```

_Protip_: If you are a Vim user, then install [Syntastic](http://www.vim.org/scripts/script.php?script_id=2736), install ESLint globally using `npm install -g eslint` and add the following line to your `.vimrc`:

```
let g:syntastic_javascript_checkers=['eslint']
```

Now you have automatic linting of your changes to JavaScript files whenever you save.

**Run testing**

To ensure your changes did not introduce any regressions you need to run the testing framework. There are four basic types of tests:

* `load` test: checks if the PDF file can be loaded without crashing
* `eq` test: a reference test that takes correctly rendered snapshots and compares them to snapshots from the current code
* `text` test: a reference test that takes snapshots of the `textLayer` overlay and compares them to snapshots from the current code
* `annotations` test: a reference test that takes snapshots of the `annotationLayer` overlay (and the underlying page) and compares them to snapshots from the current code
* `fbf` test: a forward-back-forward test
* Unit tests: Jasmine unit tests that are run separately from the above tests

**Generating reference images**

The reference tests require you to generate original snapshots for comparison. The snapshots should be generated before you make any changes. If you have already made some changes, `git stash` your work. Then make sure you have created a `browser_manifest.json` file. Copy the example browser manifest located in `test/resources/browser_manifests` to get started:

```
cp test/resources/browser_manifests/browser_manifest.json.example test/resources/browser_manifests/browser_manifest.json
```
Then edit the manifest and make sure it points to the browser(s) you want to use for generating the reference images.

Now we can generate the reference images:

```
gulp makeref
```
You can then run the test suite from the PDF.js root folder:

```
gulp test
```

**Running unit tests separately**

Unit tests are run when `gulp test` is run, but they can also be run separately two different ways:

1. In the browser. A web server has to be setup to host the PDF.js files. Tests will be executed by opening the `{url-to-pdf.js}/test/unit/unit_test.html` page. If the web server is started using the `gulp server` command, the URL will be `http://localhost:8888/test/unit/unit_test.html`.
2. Command line. `gulp unittest` will run all the tests using the regression test framework.

### 5. Push changes to your fork/branch
After lint and all tests pass, push the changes to your fork/branch on GitHub:
```
git push origin {branch_name}
```

### 6. Create pull request
Create a pull request on GitHub for your feature branch. The code will then be reviewed and tested further by our contributors and test bot.

Note that the translations for PDF.js in the `l10n` folder are synchronized with the Aurora branch of Mozilla Firefox. This means that we will only accept pull requests that add strings currently missing in the Aurora branch (as it will take at least six weeks before the most recent translations are in the Aurora branch), but keep in mind that the changes will be overwritten when we synchronize again.

### 7. Code review and automated testing
In addition to the GitHub pull request workflow, it is highly recommended that you communicate with the PDF.js team, for example via the `#pdfjs` IRC channel at `irc.mozilla.org`. That will help to find a reviewer for your patch and speed up the review process. The reviewer will kick off further testing and do a code review.

You can speed up fetching a remote GitHub branch (possibly belonging to another user) using `git try {username} {branch_name}`. Add the following to the `.git/config` file to be able to do that:
```
[alias]
  try = !sh -c 'IFS=\":\" read -ra ARGS <<< \"$0\" && git fetch https://github.com/${ARGS[0]}/pdf.js.git ${ARGS[1]} && git checkout FETCH_HEAD'
```

### 8. Merge into master
If all goes well, a collaborator will merge your changes into the main repository.