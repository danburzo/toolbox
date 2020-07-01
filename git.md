# Git recipes

## List untracked files

From [this Stack Overflow thread](https://stackoverflow.com/questions/3801321/git-list-only-untracked-files-also-custom-commands):

```bash
git ls-files --others --exclude-standard
```

## Remove untracked files

`git clean` removes untracked files from the working tree. `git clean -n` (`--dry-run`) shows a preview of the effect, and `git clean -f` (`--force`) actually deletes them. Use `-d` to delete folders as well.

## Bring in changes from another branch

`git merge --squash my-feature` brings in changes from the `my-feature` branch onto the current branch, without committing them.

## Get the most recent tag that matches a pattern

```bash
git tag --sort=-creatordate --list "v-dev-*" | head -n1
```

Only lists tags matching the `v-dev-*` pattern (e.g. `v-dev-0.1.0`). With `-creatordate` we sort the tags in descending creation date. `head -n1` picks up the first line from that output.

## Delete remote tags that match a pattern

```bash
git tag | grep "v-dev-*" | xargs -n1 -I{} git push origin :{}
```