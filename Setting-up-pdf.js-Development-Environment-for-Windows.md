## Git for Windows environment

This is the easiest and most recommended way to setup a development environment for PDF.js:

* Install Node.js from http://nodejs.org.

* Install Git for Windows from https://github.com/git-for-windows/git/releases. Note that Unix line endings must be set:

  ```> git config --global core.autocrlf input```

## Cygwin environment
Alternatively you can use [Cygwin](http://www.cygwin.com/), a collection of tools providing a basic Linux API look and feel. Download the latest package from the Cygwin website and follow the installation instructions until you reach the "Select Packages" screen. Here you should at least choose:

  * [Devel] -> git
  * [Devel] -> make

To be able to run font tests, you should also choose:

  * [Interpreters] -> python

You should now be able to fork/push your repositories. To build the project you will need to install Node.js from http://nodejs.org.

You can now continue to the [[Contributing]] page. 