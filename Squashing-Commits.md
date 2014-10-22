We try to keep the history for pdf.js relatively clean and we may ask contributors to "squash" their commits before we merge.  

**Note:**
These directions assume that you named the Mozilla pdf.js repo (not your fork) `upstream` and you have a branch called `super-feature`. See [[Contributing]] for details.

1. Add the following to your git config. Either the global one or the config within your pdf.js fork (`.git/config`).
  ```bash
  [alias]
  	squash = !sh -c 'git checkout upstream/master && git merge --no-commit --squash $0 && git checkout -B $0 && git commit -e'
  ```

1. Then you simply need to do:
  ```bash
  git merge upstream/master
  git squash super-feature
  ```

1. That will bring up your editor to allow you to put in the commit message you want. After entering a commit message, press Esc and type `:wq` to exit the editor (if the editor is set to vim).

1. Then update the pull request:
  ```bash
  git push --force origin super-feature
  ```

## Alternatives
1. Step-by-step commands
  ```
  # fetches the current upstream repository
  git fetch upstream
  # resets HEAD to the current upstream
  git checkout upstream/master
  # merges all commits from the local branch
  git merge --no-commit --squash super-feature
  # re-creates the branch starting from current HEAD (old commits will be lost)
  git checkout -B super-feature
  # lets you edit the commit and checks in the changes (you can also use git commit -m "message")
  git commit -e
  # pushes the changes (in general, be careful with the --force parameter)
  git push --force origin super-feature
  ```

1. <a name="simple"></a>Or, you can use rebase. Let's say you have 5 commits to squash and you don't have merge commits:
  ```
  git rebase -i HEAD~5
  ```
  Change `pick` to `squash` (or `fixup`) for last four and update the commit message in the editor, then `git push --force origin super-feature`.

## (Recovering from bad squashes)

Hopefully you did not do anything wrong, then you don't need to read this section :) If you did something wrong and you end up with lots of commits you don't recognize. Don't panic:

1. Find your _last_ commit sha/id before you did squashing (e.g. 'abcde123'). The pull request github page will help you with that in the list of the commits (or diff comments). And then just run:

  ```
  git commit -B super-feature abcde123
  ```

2. Or, you can just cherry-pick your commits into up-to-date upstream master (e.g. you see 'abcdef123' and 'defghi567' as your commits):

  ```
  # fetches the current upstream repository
  git fetch upstream
  # reset your branch to upstream master
  git checkout -B super-feature upstream/master
  # cherry-pick only your commits and resolve conflicts
  git cherry-pick abcdef123
  git cherry-pick defghi567
  # optionally rebase can be run, in this case git rebase -i HEAD~2
  ```

And repeat squashing.