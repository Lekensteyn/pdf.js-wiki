## MSYS Environment

The simplest way to setup the development environment for the pdf.js project:

* Git for Windows (http://code.google.com/p/msysgit/, the Unix line endings must be set)

```> git config --global core.autocrlf input```

* Mozilla build environment (http://ftp.mozilla.org/pub/mozilla.org/mozilla/libraries/win32/MozillaBuildSetup-Latest.exe)

* Node.js (http://nodejs.org/)

If the Visual Studio is not installed or to avoid switching between the git bash and the Mozilla build environment, modify any startXXX.cmd file in the c:\mozilla-build to look like https://gist.github.com/1518181 .

## Cygwin Environment
Another way to setup an development environment for the pdf.js project is to use [Cygwin](http://www.cygwin.com/) which is a collection of tools providing basic Linux API look and feel.
Download the latest 'setup.exe' file from Cygwins website, and follow the install instructions until you reach the "Select Packages" screen. Here you should at least choose:

  * [Devel] -> git
  * [Devel] -> make
  * [Interpreters] -> python

You should now be able to fork/push your repositories. To build the project you'll need to install node.js from http://nodejs.org/.

## gjslint Install

Also, you will need "gjslint", which can be installed as an [easy_install](http://peak.telecommunity.com/DevCenter/EasyInstall#installing-easy-install) package using:

```> easy_install http://closure-linter.googlecode.com/files/closure_linter-2.3.5.tar.gz```

(Note: version 2.3.6 is [[bad|http://code.google.com/p/closure-linter/issues/detail?id=50&thanks=50&ts=1342745700]])

from your new shell (MSYS, Cygwin Bash Shell). With these tools you should be able to build/hack/etc. the rep.


See also [[Contributing]] and https://github.com/mozilla/pdf.js. 