## MSYS Environment

The easiest way to setup the development environment for the PDF.js project:

* Node.js (http://nodejs.org)

* Git for Windows (https://github.com/git-for-windows/git/releases); note that Unix line endings must be set:

  ```> git config --global core.autocrlf input```

## Cygwin Environment
Another way to setup a development environment for PDF.js is to use [Cygwin](http://www.cygwin.com/) which is a collection of tools providing basic Linux API look and feel. Download the latest 'setup.exe' file from Cygwins website and follow the install instructions until you reach the "Select Packages" screen. Here you should at least choose:

  * [Devel] -> git
  * [Devel] -> make
  * [Interpreters] -> python

You should now be able to fork/push your repositories. To build the project you will need to install Node.js from http://nodejs.org.

See also [[Contributing]] and https://github.com/mozilla/pdf.js. 