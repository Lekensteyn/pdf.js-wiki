PDF.js maintains two bots that perform various tasks for pull requests. The bots are controlled by the owners and selected collaborators of the project. We list the characteristics of both bots and describe the tasks that they are able to perform.

Tasks
-----

While we use Travis CI for linting, we use the bots for all other tasks like generating a preview for a pull request and running unit, font and reference tests. The available bot commands are listed below.

- `preview` (generates a preview build for the pull request)
- `lint` (runs the linting tool)
- `unittest` (runs the unit tests)
- `fonttest` (runs the font tests)
- `test` (runs all tests, i.e., the unit tests, font tests and reference tests)
- `makeref` (generates new reference images for the reference tests, for instance when a pull request changes the rendering of some PDFs)

Characteristics
---------------

We have a Linux and a Windows bot. The Linux bot runs Ubuntu 12.04.4 LTS with Xvfb, whereas the Windows bot runs Windows Server Datacenter (service pack 2). The Linux bot has a few additional font packages to improve font rendering:

- `latex-cjk-all`
- `xfonts-wqy`
- `fonts-arphic-ukai`
- `fonts-arphic-uming`
- `fonts-ipafont-mincho`
- `fonts-ipafont-gothic`
- `fonts-unfonts-core`