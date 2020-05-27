# Unix command-line tools

The standard command-line tools available on Unix-based systems are wonderful, if occasionally inscrutable. This page contains some commands I found useful.

_Note:_ I'm writing these commands on macOS and while they're almost always identical across all Unix-based systems there _are_ some (small) differences in the tools that come with the operating system. Some options from Linux may not be available on macOS, or viceversa.

## Tools used

* [`awk`](https://en.wikipedia.org/wiki/AWK)
* [`diff`](https://en.wikipedia.org/wiki/Diff)
* [`find`](https://en.wikipedia.org/wiki/Find_(Unix))
* [`grep`](https://en.wikipedia.org/wiki/Grep)
* [`join`](https://en.wikipedia.org/wiki/Join_(Unix))
* [`sed`](https://en.wikipedia.org/wiki/Sed)
* [`sort`](https://en.wikipedia.org/wiki/Sort_(Unix))
* [`uniq`](https://en.wikipedia.org/wiki/Uniq)
* [`wc`](https://en.wikipedia.org/wiki/Wc_(Unix))
* [`xargs`](https://en.wikipedia.org/wiki/Xargs)

You can read about the available options for any tool by running `man`:

```bash
man <command>
```

> 👉 The `man` help pages can sometimes be hard to understand. [`tldr`](https://github.com/tldr-pages/tldr) is a community-driven effort to offer clearer examples of each command, so you might want to look into it.

## General tidbits

### Adding a newline character to a command argument

Use the `$'…'` format to have `\n` be interpreted as a newline character.

```bash
my-command --text=$'Hello\nWorld'
```

## Tricks to aid refactoring

I found these commands useful for poking around a large codebase.

### Sort files by number of lines

This command sorts all JavaScript files in the current folder by their line count, from the largest file to the smallest.

```bash
find . -name '*.js' | xargs wc -l | sort -r
```

Example output:

```
   92573 total
    3203 js/first-file.js
    2443 js/second-file.js
    1858 js/third-file.js
    ...
```

How it's built:

1. `find` all JavaScript files (`*.js`) in the current (`.`) folder
2. pass the results, via `xargs`, to the line counter (`wc`)
3. `sort` the line count report from largest to smallest (`-r`)

#### Dealing with spaces in file names

For the command to work with spaces in file names, we need to make `find` and `xargs` work better together by using these options:

* `-print0` makes `find` print all the file names in one line, separated by _null characters_, instead of the default new-line character.
* `-0` makes `xargs` assume that the inputs are separated by the _null character_ instead of a white-space character (i.e. the new-line character used by default in `find`)

The command now looks like this:

```bash
find . -name '*.js' -print0 | xargs -0 wc -l | sort -r
```


### Find all unique occurrences of a certain pattern

This command looks at code that matches the pattern "console._something_()" and extracts all the different `something`s.

```bash
find . -name '*.js' | xargs perl -nle 'print $1 if /console\.([a-z]+)\(/i' | sort -u
```

Example output:

```
error
info
log
time
timeEnd
trace
warn
```

How it's built:

1. `find` all JavaScript files (`*.js`) in the current directory (`.`)
2. pass the file names to a `perl` command that extracts a RegExp pattern
3. finally, `sort` the extracted patterns to show only `-u`nique occurrences

> 💡 To make the command work with files that contain spaces in their name, we'll need to use [the `-print0` / `-0` combo](#dealing-with-spaces-in-file-names) again.

#### The `perl` part

> Unix-based systems have another tool for matching patterns, called `grep`. However, `grep` on macOS doesn't have an option [to extract just _a part of a RegExp_](https://superuser.com/questions/1355777/grep-on-macos-find-unique-occurrences-of-a-capturing-group-in-regular-expressio), so we need to use `perl` for this.

Glossing over the `-nle` arguments to the `perl` command ([about which you can read here](http://perldoc.perl.org/perlrun.html)), the code looks for the pattern:

```js
/console\.([a-z]+)\(/i
```

And prints the first _capturing group_ (`[a-z]+`) out of the regular expression.

#### Variation: find most frequent occurrences of a certain pattern

Here, instead of finding the list of unique occurrences of a certain pattern, we count how many time a certain pattern occurs.

```bash
find . -name '*.js' | xargs perl -nle 'print $1 if /console\.([a-z]+)\(/i' | sort | uniq -c | sort -nr
```

The command will result in something like:

```
  85 log
  65 error
  52 warn
  19 time
  17 timeEnd
   9 info
   6 trace
```

The `find` and `perl` parts are the same, but we've replaced `sort -u` with:

1. A simple `sort` to sort the occurrences alphabetically, then
2. `-c`ount the occurrences of `uniq`ue patterns, then
3. `sort` the patterns again by the number of occurrences (`-n`umeric and `-r`reversed)

### Find the most frequently changed files

This command is adapted from [Software Design X-Rays](https://pragprog.com/book/atevol/software-design-x-rays) by Adam Tornhill: 

```bash
git log --name-only --diff-filter=M --format=format: | grep -ve '^$' | sort | uniq -c | sort -r
```

For this repo you're reading, it gives us these results:

```
  89 README.md
  10 journal.md
   7 typefaces.md
   4 writing.md
   2 oblique.md
   2 ffmpeg.md
   1 unix-cli.md
   1 react.md
   1 adobe.md
```

Let's unpack how it's built:

#### The `git` part

* `git log` shows us the commit history for the current branch in the repository.
* `--format=format:`, i.e. _use a custom format that is the empty string_, is a trick to remove the commit information (author, date, message, etc.) from the log.
* `--name-only` shows the files included in each commit.
* `--diff-filter=M` shows us only the file that have been `M`odified, thus it excludes files from commits where they've been `A`dded or `R`emoved.

#### The `grep` part

The `git log` will contain empty lines between the commits; we'll exclude them from our count using `grep`.

We'll use a regular expression (`-e`). The `^$` pattern (_start of line_ immediately followed by _end of line_) matches any empty line, but by using the `-v` flag to invert the pattern we can pick only the lines that _don't_ match, i.e. are not empty.

#### The `sort` / `uniq` part

* `sort` the lines
* `-c`ount the occurrences of `uniq`ue lines
* `sort` the lines again based on the count, `-r`eversed (from largest count to lowest count)

#### Variation: only count changes on files that match a certain pattern

If we replace `grep -ve '^$'` with `grep -e 'some pattern'`, we can limit our count to files whose names match a pattern. For example, targeting JavaScript files with `grep -e '\.js$'` — notice we've removed the `-v` (invert) flag. The full command becomes:

```bash
git log --name-only --diff-filter=M --format=format: | grep -e '\.js$' | sort | uniq -c | sort -r
```

### Sort files by number of lines changed on a Git branch

```bash
git diff --stat origin/master HEAD | awk '{ print $3, $1 }' | sort -rn
```

### Find the differences between the output of two commands

The general formula is: 

```bash
diff <( ... command 1 goes here ... ) <( ... command 2 goes here ... )
```

It works even with `curl` (the `-s` is for silent):

```bash
diff <(curl -s http://example.com/1) <(curl -s http://example.com/2)
```

### Find files who don't have counterparts, and create them

Some static site generators' multilanguage features work by creating separate Markdown files for each language, e.g. `about.md` for English and `about.de.md` for German.

To find which `.md` files don't have their equivalent `.de.md` file:

```bash
join -v 1 \
  <(find . -name "*.md" -not -name "*.de.md" | sort) \
  <(find . -name "*.de.md" | sed -E "s/\.de\.md/\.md/" | sort)
```

The first `find` gets us the list of `.md` files in English (i.e. Markdowns that don't end in `.de.md`). 

The second `find` gets us the list of `.md` files in German (ending in `*.de.md` ), then we use `sed` to replace `.de.md` with `.md`. 

> Note: We `sort` the output of both `find` commands, because the `join` command expects it. But in this case, both being the output of a `find` command, it may not be needed?

The `join -v 1` prints out all the lines in `file 1` (English) which are not matched by a line in `file 2` (German). 

Now, let's copy over the English version for German files we haven't found:

```bash
join -v 1 \
  <(find . -name "*.md" -not -name "*.de.md" | sort) \
  <(find . -name "*.de.md" | sed -E "s/\.de\.md/\.md/" | sort) \
  | sed "p;s/\.md/\.de\.md/" | xargs -n2 cp
```

We reach for `sed` once more to produce the the original line (with `p;`), followed by the same line with `.md` changed back to `.de.md`. With this input:

```
my-file.md
my-other-file.md
```

we get:

```
my-file.md
my-file.de.md
my-other-file.md
my-other-file.de.md
```

`xargs` takes the input two lines at a time (`-n2`) and uses them as the first, and the second argument to `cp`, respectively. Something like:

```bash
cp my-file.md my-file.de.md
cp my-other-file.md my-other-file.de.md
```

Alternatively we can use the `-n` option in `cp`, which only makes a copy of the file if the destination file doesn't already exist, to avoid having to run two separate `find`s and a `join`:

```bash
find . -name "*.md" -not -name "*.de.md" | sed "p;s/\.md/\.de\.md/" | xargs -n2 cp -n
```

