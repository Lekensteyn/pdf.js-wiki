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
git squash super-feature
```
1. That will bring up your editor allow you to put in the commit message you want.
1. Then update the pull request:
```bash
git push --force origin super-feature
```

## Alternatives
1. Step-by-step commands
```
# resets HEAD to the current upstream
git checkout upstream/master
# merges all commits from the local branch
git merge --no-commit --squash super-feature
# re-creates the branch starting from current HEAD (old commits will be lost)
git checkout -B super-feature
# lets you edit the commit and checks in the changes
git commit -e
```

1. Or, you just use rebase (let's say you have 5 commits to merge)
```
git rebase -i HEAD~5
```
Change pick to squash for last four and update the commit message.