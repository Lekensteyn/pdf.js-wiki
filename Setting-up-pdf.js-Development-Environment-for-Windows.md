## MSYS Environment

The simplest way to setup the development environment for the PDF.js project:

* Node.js (http://nodejs.org)

* Git for Windows (https://github.com/git-for-windows/git/releases; Unix line endings must be set)

  ```> git config --global core.autocrlf input```

* Mozilla build environment (http://ftp.mozilla.org/pub/mozilla.org/mozilla/libraries/win32/MozillaBuildSetup-Latest.exe)

If Visual Studio is not installed or to avoid switching between the Git bash and the Mozilla build environment, modify any startXXX.cmd file in C:\mozilla-build to look like https://gist.github.com/1518181.

## Cygwin Environment
Another way to setup a development environment for PDF.js is to use [Cygwin](http://www.cygwin.com/) which is a collection of tools providing basic Linux API look and feel. Download the latest 'setup.exe' file from Cygwins website and follow the install instructions until you reach the "Select Packages" screen. Here you should at least choose:

  * [Devel] -> git
  * [Devel] -> make
  * [Interpreters] -> python

You should now be able to fork/push your repositories. To build the project you will need to install Node.js from http://nodejs.org.

See also [[Contributing]] and https://github.com/mozilla/pdf.js. 