To publish the current pdf.js to the gh-pages branch:

# make sure the stable version is loaded
$ make web
# run 'make server' and verify http://localhost:8888/build/gh-pages/web/viewer.html
$ cd build/gh-pages
$ git commit
# ... add commit message
$ git push