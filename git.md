# Git recipes

## Remove untracked files

`git clean` removes untracked files from the working tree. `git clean -n` (`--dry-run`) shows a preview of the effect, and `git clean -f` (`--force`) actually deletes them. Use `-d` to delete folders as well.

## Bring in changes from another branch

`git merge --squash my-feature` brings in changes from the `my-feature` branch onto the current branch, without committing them.