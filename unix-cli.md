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

### Change files from JSON to JS modules

To work around the limitations of the format, I needed to convert hundreds of files from JSON to JS modules that export plain objects. 

#### Step 1: batch rename

As a variation of the previous pattern, to rename (i.e. move) files matching a certain pattern:

```bash
find . -name "*.json" | sed "p;s/\.json/\.data\.js/" | xargs -n2 mv
```

#### Step 2: add in `export default`

We want to change the files from:

_sample.json_
```json
{
  "some_key": "some_value"
}
```

to:

_sample.data.js_
```js
module.exports = {
  "some_key": "some_value"
}
```

For this, we'll use `sed` to replace the content of the first line:

```bash
find . -name '*.data.js' | xargs -n1 sed -i "" '1s/^.*$/export default \{/'
```

* the `-i` flag instructs `sed` to make the substitution in-place (in the same file); for the BSD version of `sed` that ships with macOS, doing that without making backup files [is done with `-i ""`](https://unix.stackexchange.com/questions/401905/bsd-sed-vs-gnu-sed-and-i);
* the `1` applies the `s`(ubstitute) command to the first line in each file, and the `^.+$` regular expression matches the entire line.

Note: when addressing specific lines, we _must_ use the `-n1` flag on `xargs` to have `sed` run on each individual file. We want:

```bash
sed file1
sed file2
sed file3
# etc.
```

Instead of:

```bash
sed file1 file2 file3 ...
```

Because the line addressing _works cumulatively_ across all input files, meaning `1` only matches the first line in the first file. 

#### Step 3: add an `import` statement

One of the reasons to switch from JSON to JS was to make some strings amenable to localization. For that I needed to add an import statement at the beginning of each file:

```js
import { t } from 'js/i18n';

// rest of the file.
```

A word of caution about the `sed` that comes with macOS:

* [it doesn't have a flag to show its version](https://stackoverflow.com/questions/37639496/how-can-i-check-the-version-of-sed-in-os-x); it's also probably pretty old;
* [it's a bit awkward about inserting `\n` characters](https://www.linuxquestions.org/questions/linux-software-2/sed-insert-a-newline-why-does-not-it-work-158806/#post5137548)

##### First attempt: a false start

To match the beginning of the first line in sed, we can use `1s/^/.../`. We'd like to add our import statement there, followed by a couple of newline breaks. At this point, I was convinced there's no way to coerce macOS `sed` to insert newlines, so I'm thinking: MacBook keyboards come with a suprinsingly-handy `§` button, can we work around the `\n` problem by using the separate `tr` program? Something like:

```bash
sed "1s#^#import { t } from 'js/i18n';§§#" my-file.data.js | tr § '\n'
```

There's a lot going on, so let's unpack it. For the `sed` part:

* `1` addresses the first line in the file;
* `s` is the substitute command, used here with the `#` character instead of the customary `/` character (you can use any other character, for that matter), because we have the latter as part of our replacemenet text and it makes things a bit easier to read;
* `^` matches the beginning of the line;
* after the replacement text, we add `§§` which are supposed to become a couple of newline characters.

Since we want to pipe the `sed` output to the `tr` command — which will replace each occurrence of the `§` character with `\n` — we're not using the `-i` (in-place) flag like before.

And here's our first roadblock. If we were to pipe the output back to the original file (like `-i` did before):

```bash
sed "1s#^#...§§#" my-file.data.js | tr § '\n' > my-file.data.js
```

We'd notice that `my-file.data.js` ends up empty. That's because redirecting `stdout` to our file via the `>` operator [immediately opens (and truncates) our file](https://unix.stackexchange.com/questions/591855/writing-to-same-file-as-part-of-a-for-loop-generates-an-empty-file) before `sed` even has the chance to read it. 

There's a command called `sponge` that you need to install separately (with `brew install moreutils`) [for this exact purpose](https://unix.stackexchange.com/questions/207919/sponge-from-moreutils-whats-the-difference-to-shell-redirect-useful-examples):

```bash
sed "1s#^#...§§#" my-file.data.js | tr § '\n' | sponge my-file.data.js
```

But using `sponge` introduces a new dependency, surely there must be some sort of POSIX command, or a combination thereof, to obtain a similar result. [`tee`](https://en.wikipedia.org/wiki/Tee_(command)) sounds like it would allow you to write back to the original file:

```bash
sed "1s#^#...§§#" my-file.data.js | tr § '\n' | tee my-file.data.js
```

But the way `tee` works makes it [an unreliable replacement for `sponge`](https://stackoverflow.com/questions/33638511/differences-between-sponge-and-tee), and it does seem like vanilla alternatives [revolve around writing to a temporary file](https://unix.stackexchange.com/questions/543541/is-there-a-standard-alternative-to-sponge-to-pipe-a-file-into-itself), then `mv`-ing it over the original file. Ugh. 

We're already stuck, and we haven't even figured out how to make this idea work on a whole batch of files, since running [multiple commands with `xargs`](https://unix.stackexchange.com/questions/56734/xargs-using-same-argument-in-multiple-commands) entails writing the compound command as a string and running it with `sh`, making the entire command something along the lines of:

```bash
find . -name '*.data.js' | xargs -n1 -I__FILE__ sh -c "sed \"1s#^#import { t } from 'js/i18n';§§#\" __FILE__ | tr § '\n' | sponge __FILE__"
```

Yikes!

##### Second attempt: a light at the end of the tunnel

Sometimes you read the wrong Stack Overflow answer, or read the right answer poorly, and off you go on a false premise. 

It turns out you actually [_can_ insert `\n` characters](https://stackoverflow.com/questions/723157/how-to-insert-a-newline-in-front-of-a-pattern) with `sed` on macOS?! Our struggle resolves to this pithy one- (well, technically two-) liner:

```bash
find . -name '*.txt' | xargs -n1 \
sed -i "" $'1s#^#import { t } from \'js/i18n\';\\\n\\\n#'
```

Using `$'...'` makes the whole sed command a C-style string which replaces `\\` with `\` and `\n` with a literal newline, making it equivalent to:

```
1s#^#import { t } from 'js/i18n';\
\
#
```

> For the sake of completeness, you might also want to take a look at [using `cat` and `echo` to prepend a line](https://www.commandlinefu.com/commands/view/14354/prepend-text-to-a-file). 

#### Step 5: replace some things with some other things

Okay, now that we've imported the `t` function, let's apply it to some strings in our JS file; that is, to turn this:

```js
import { t } from 'js/i18n';

module.exports = {
  "some_key": "some_value"
}
```

to this:

```js
import { t } from 'js/i18n';

module.exports = {
  "some_key": t`some_value`
}
```

This is done by capturing `some_value` and using a back-reference to wrap `t` around it:

```bash
find . -name '*.txt' | xargs -n1 \
sed -E 's/("mykey"): "([^"]*)"/\1: t`\2`/g'
```

[By default, `sed` works with BRE](https://stackoverflow.com/questions/4453760/how-to-escape-plus-sign-on-mac-os-x-bsd-sed) (basic regular expressions), which lack some of the comforts of their modern counterparts. Running it with the `-E` flag interprets regular expressions as _extended_.

> Note: we match `some_value` by `[^"]*`, i.e. a sequence of zero or more non-quote characters. This is not entirely correct, as JavaScript strings can contain (escaped) quote characters, or span multiple lines.