# `wget` Recipes

## Introduction

## Installation

## Recipes for website mirroring / scraping

Here are some useful tricks with `wget`. [More of them here](http://www.labnol.org/software/wget-command-examples/28750/).

### Mirror a website

```
wget --mirror --no-clobber --no-parent --wait=3 --execute robots=off --domains=danburzo.ro,assets.danburzo.ro --user-agent=Mozilla danburzo.ro
```

A quick explanation for these flags: 

* `--mirror` is a shorthand for `-r -N -l inf --no-remove-listing`, which are some switches useful for scraping
* `--no-clobber` instructs wget not to fetch each occurrence of the same URL as a separate file
* `--no-parent` don't go up the hierarchy
* `--wait=seconds` is used to wait for N seconds between requests, a.k.a. being nice to the server
* `--execute robots=off` will ignore the `robots.txt` file on the website and any `nofollow` attributes on links
* `--domains=domain1,domain2,...` is a list of domain names to consider when crawling (you'll want to include here any domains that hold the assets for the page)
* `--user-agent=UserAgentString` can be used in case the server blocks access based on the User Agent

### Download sequential URLs

```
wget http://example.com/records/{1..1000}
```

### Download a list of URLs

The URLs can be specified in a separate file `list-of-URLs.txt`, with one URL per line.

```
wget --input list-of-URLs.txt
```

## Further reading

* [Pre-rendering static websites with `wget`](https://apex.sh/blog/post/pre-render-wget/)
