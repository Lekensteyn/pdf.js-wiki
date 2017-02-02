1. Install git https://git-scm.com/download/win
1. Install msys2 and copy 'zip' from mys2's bin to git's (TODO: maybe we should start with msys2)
1. Install python 2.7 https://www.python.org/downloads/windows/
  1. Ensure installer adds it to the path
1. Install node js lts https://nodejs.org/en/
1. Install botio from cloned repo (the npm package is not up to date)
  1. git clone https://github.com/arturadib/botio.git
  1. cd botio
  1. modify package

    ```diff
    diff --git a/package.json b/package.json
    index ad583af..fca270b 100644
    --- a/package.json
    +++ b/package.json
    @@ -25,7 +25,7 @@
         "commander": "0.5.2",
         "express": "2.5.8",
         "request": "2.9.153",
    -    "shelljs": "latest"
    +    "shelljs": "0.0.5pre4"
       },
       "devDependencies": {},
    ```
  1. npm install -g .
1. Install bot files
  1. `git clone https://github.com/mozilla/botio-files-pdfjs.git`
  1. edit config.json
1. Setup pdfjsbot github access token
1. Start the bot `botio start --user pdfjsbot --pwd <github access token>`
1. Setup webhooks on github
