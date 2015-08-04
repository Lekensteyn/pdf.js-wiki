## MSYS Environment

The simplest way to setup the development environment for the PDF.js project:

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

See also [[Contributing]] and https://github.com/mozilla/pdf.js. 