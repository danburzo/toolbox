# Toolbox

This is a collection of tricks, tools, libraries, APIs and data sources for creative projects. It's a reference as well as a compendium of things you can do in the browser and the command line.

Although this is a list of mostly Github-hosted tools, it's different from [`awesome-*`](https://github.com/sindresorhus/awesome) lists in that I try to avoid having several things with overlapping purposes and only include what I consider to be the excellent ones: tools that are easy to install, elegant to work with, and well documented &mdash; plus some quirky outliers for good fun.

I've been inspired to keep this list, and name it as such, by [javierarce/toolbox](https://github.com/javierarce/toolbox), which serves a similar purpose and contains great resources that I recommend you check out. 

Contributions to this list are welcome via [issues](https://github.com/danburzo/toolbox/issues) and [pull requests](https://github.com/danburzo/toolbox/pulls) &mdash; I'm always looking for new ideas!

Thanks for stopping by. ✌️

## Table of Contents

* [JavaScript libraries](#javascript-libraries)
	* [Image processing, OCR](#image-processing-optical-character-recognition-ocr)
	* [Drawing, illustration, motion](#drawing-illustration-motion)
	* [Data visualization](#data-visualization)
	* [3D, Virtual Reality](#3d-vr)
	* [Audio](#audio)
	* [User Interfaces](#user-interfaces)
	* [Mapping](#mapping)
	* [Gamemaking](#gamemaking)
	* [Working with documents](#working-with-documents)
	* [Algorithms, data structures](#algorithms-data-structures)
	* [Sensible app architecture](#sensible-app-architecture)
	* [Web scraping, data extraction](#web-scraping-data-extraction)
	* [Language processing](#language-processing)
* [Data sets](#data-sets)
	* [Language](#language)
	* [Geographical data](#geographical-data)
	* [Miscellaneous datasets](#miscellaneous-datasets)
* [APIs](#apis)
* [Command-line tools](#command-line-tools)
* [Online tools](#online-tools)
* [Miscellaneous tips & tricks](#miscellaneous-tips--tricks)
	* [Start a server for a folder](#start-a-server-for-a-folder)
	* [Fetch a file from the web](#fetch-a-file-from-the-web)
	* [Make an S3 bucket publicly available](#make-an-s3-bucket-publicly-available) 
	* [`wget` for website mirroring / scraping](#wget-for-website-mirroring--scraping)

## JavaScript libraries

### Image processing, optical character recognition (OCR)

#### [quaggaJS](https://github.com/serratus/quaggaJS)

> __QuaggaJS is a barcode-scanner entirely written in JavaScript__ supporting real-time localization and decoding of various types of barcodes such as EAN, CODE 128, CODE 39, EAN 8, UPC-A, UPC-C, I2of5 and CODABAR. The library is also capable of using `getUserMedia` to get direct access to the user's camera stream. Although the code relies on heavy image- processing even recent smartphones are capable of locating and decoding barcodes in real-time.
 
For reading barcodes with a webcam or phone camera. See also __[JSBarcode](https://github.com/lindell/JsBarcode)__ for _generating_ barcodes.

#### [omggif](https://github.com/deanm/omggif)

> JavaScript implementation of a GIF 89a encoder and decoder.

For making GIFs. [Animated_GIF](https://github.com/sole/Animated_GIF), for example, builds on top of this library.

#### [exif.js](https://github.com/jseidelin/exif-js)

> JavaScript library for reading EXIF image metadata.

Extracting information from JPEG files.

#### [Lanczos.js](https://github.com/mudcube/Lanczos.js)

> Lancszos image resampling.

This is for resizing images nicely in the browser.

#### [tesseract.js](https://github.com/naptha/tesseract.js)

> Tesseract.js is a javascript library that gets words in almost any language out of images.


### Drawing, illustration, motion

#### [chroma.js](https://github.com/gka/chroma.js)

> JavaScript library for all kinds of color manipulations.

Converting a color from and to any format, generate pleasing color palettes and color variations. See also [TinyColor](https://github.com/bgrins/TinyColor).

#### [paper.js](https://github.com/paperjs/paper.js)

> The Swiss Army Knife of Vector Graphics Scripting.

#### [two.js](https://github.com/jonobr1/two.js)

> A renderer-agnostic two-dimensional drawing API for the web.

#### [opentype.js](https://github.com/nodebox/opentype.js)

> Read and write OpenType fonts using JavaScript.

#### [snap.svg](https://github.com/adobe-webplatform/Snap.svg) 

> The JavaScript library for modern SVG graphics.

#### [p5.js](https://github.com/lmccart/p5.js)

> A JS client-side library for creating graphic and interactive experiences, based on the core principles of Processing.

#### [rune.js](https://github.com/runemadsen/rune.js) 

> A JavaScript library for programming graphic design systems with SVG.

#### [mojs](https://github.com/legomushroom/mojs) 

> motion graphics toolbelt for the web

#### [matter-js](https://github.com/liabru/matter-js) 

> A 2D rigid body physics engine for the web 

#### [ccapture.js](https://github.com/spite/ccapture.js/) 

> A library to capture canvas-based animations at a fixed framerate.

### Data visualization


#### [d3](https://github.com/mbostock/d3) 

> A JavaScript visualization library for HTML and SVG.

This is the tool of choice for any data visualization project. To draw standard charts with D3, take a look at [MetricsGraphics](https://github.com/mozilla/metrics-graphics), [plottable](https://github.com/palantir/plottable), or [d3plus](https://github.com/alexandersimoes/d3plus), all of which are built on top of it. [awesome-d3](https://github.com/wbkd/awesome-d3) is useful for learning what other things you can do with D3.

#### [cytoscape.js](https://github.com/cytoscape/cytoscape.js) ([website](http://js.cytoscape.org/))

> Graph theory (a.k.a. network) library for analysis and visualisation.

#### [dagre](https://github.com/cpettitt/dagre) 

> Directed graph renderer for JavaScript 

Built on top of [graphlib](https://github.com/cpettitt/graphlib) by the same author, `dagre` helps you build directed graphs that you can then plug into D3 or cytoscape. See [the excellent wiki](https://github.com/cpettitt/dagre/wiki) for details.

### 3D, VR

#### [three.js](https://github.com/mrdoob/three.js/) ([website](https://threejs.org/))

> JavaScript 3D library.

Much like D3 is the tool of choice for data visualization, three.js is the established library for working in 3D. See also [pre3d](https://github.com/deanm/pre3d/) (although it hasn't been worked on in ages).

#### [regl](https://github.com/mikolalysenko/regl) ([website](http://regl.party/))

> Fast functional WebGL. 

#### [aframe](https://github.com/aframevr/aframe/) ([website](https://aframe.io/))

> Building blocks for the VR Web.

### Audio

#### [paulstretch.js](https://github.com/sebpiq/paulstretch.js)

> This is a JavaScript implementation - with a few improvements - of Paul's Extreme Sound Stretch algorithm (Paulstretch) by Nasca Octavian PAUL.

#### [tuna](https://github.com/Dinahmoe/tuna) 

> An audio effects library for Web Audio.

#### [Tone.js](https://github.com/Tonejs/Tone.js) 

> A Web Audio framework for making interactive music in the browser. 

#### [MIDI.js](https://github.com/mudcube/MIDI.js) 

> Making life easy to create a MIDI-app on the web.

#### [Gibberish](https://github.com/charlieroberts/Gibberish) ([website](http://www.charlie-roberts.com/gibberish/))

> Fast, JavaScript DSP library that creates JIT optimized audio callbacks using code generation techniques

Library behind [Gibber](https://github.com/charlieroberts/Gibber) ([website](http://gibber.mat.ucsb.edu/)) &mdash; an audiovisual live coding environment for the browser. See also [interface.js](https://github.com/charlieroberts/interface.js) ([website](http://www.charlie-roberts.com/interface/)) by the same author &mdash; a GUI library for music / arts applications that works with touch, mouse and motion events. 

#### [genish.js](https://github.com/charlieroberts/genish.js) ([website](http://www.charlie-roberts.com/genish/))

> A library for generating optimized, single-sample audio callbacks in JavaScript. Inspired by gen~ in Max/MSP.

#### [howler.js](https://github.com/goldfire/howler.js) ([website](https://howlerjs.com/))

> howler.js is an audio library for the modern web. It defaults to Web Audio API and falls back to HTML5 Audio. This makes working with audio in JavaScript easy and reliable across all platforms.

#### Dig deeper

* [awesome-webaudio](https://github.com/notthetup/awesome-webaudio)
* [web-audio-resources](https://github.com/alemangui/web-audio-resources)

### User Interfaces

#### [zingtouch](https://github.com/zingchart/zingtouch) 

> A JavaScript touch gesture detection library for the modern web

### Mapping

#### [leaflet.js](https://github.com/Leaflet/Leaflet) 

> JavaScript library for mobile-friendly interactive maps.

#### [Stamen maps](https://github.com/stamen/maps.stamen.com) 

> This is the code behind the Stamen maps site, which shows off our custom tiles and explains how to get them into other sites.

#### [turf.js](https://github.com/Turfjs/turf) 

> A modular geospatial engine written in JavaScript.

### Gamemaking

#### [coquette](https://github.com/maryrosecook/coquette) 

> A micro framework for JavaScript games. Handles collision detection, the game update loop, canvas rendering, and keyboard and mouse input.

### Working with documents

#### [pdf.js](https://github.com/mozilla/pdf.js/) 

> PDF reader in JavaScript.

#### [pdf2json](https://github.com/modesty/pdf2json) 

> A PDF file parser that converts PDF binaries to text-based JSON, powered by a fork of pdf.js

#### [pdfkit](https://github.com/devongovett/pdfkit) 

> A JavaScript PDF generation library for Node and the browser

#### [jsPDF](https://github.com/MrRio/jsPDF) 

> Generate PDF files in JavaScript. 

#### [epub.js](https://github.com/futurepress/epub.js/) 

> EPUBs in the browser.

#### [magicbook](https://github.com/magicbookproject/magicbook) 

> It aims to be the best free tool for creating print and digital books from a single source.

### Algorithms, Data structures

#### [graphlib](https://github.com/cpettitt/graphlib) 

> A directed multi-graph library for JavaScript.

#### [brain](https://github.com/harthur/brain) 

> Neural networks in JavaScript.

### Sensible app architecture


#### [backbone](https://github.com/jashkenas/backbone) ([website](http://backbonejs.org/))

> Give your JS App some Backbone with Models, Views, Collections, and Events.

#### [vue](https://github.com/vuejs/vue) ([website](http://vuejs.org/))

> Simple yet powerful library for building modern web interfaces.

A lightweight alternative to Angular or React.

#### [Bluebird](https://github.com/petkaantonov/bluebird) 

> Bluebird is a full featured promise library with unmatched performance.

#### [hackathon-starter](https://github.com/sahat/hackathon-starter) 

> A boilerplate for Node.js web applications

### Web scraping, data extraction

#### [artoo](https://github.com/medialab/artoo) 

> artoo.js is a piece of JavaScript code meant to be run in your browser's console to provide you with some scraping utilities. 

Allows you to create custom bookmarklets to scrape a web page from your browser; I could see this being used in places where on a server you'd have to jump through some hoops, e.g. getting your Facebook saved links.

#### [x-ray](https://github.com/lapwinglabs/x-ray) 

> The next web scraper. See through the `<html>` noise.

From the maker of [cheerio](https://github.com/cheeriojs/cheerio), and built on top of it, x-ray gives you a terse, fluent API to scrape and navigate pages.

#### [fathom](https://github.com/mozilla/fathom) 

> A framework for extracting meaning from web pages. 

Seems to be still a work in progress, but it will ultimately be a tool for understanding where some particular type of content is on a page: "Where is the body? The title? Is this a "next page" button? Is this a comment form, and are there comments here? By better understanding the parts of a page, we can improve our understanding of how a user interacts with it." ([source](https://wiki.mozilla.org/Context_Graph#Fathom))

#### [readability](https://github.com/mozilla/readability) 

> A standalone version of the readability library used for Firefox Reader View. 

Extract the main content from a web page.

### Language processing

#### [natural](https://github.com/NaturalNode/natural)

> "Natural" is a general natural language facility for nodejs. Tokenizing, stemming, classification, phonetics, tf-idf, WordNet, string similarity, and some inflections are currently supported. At the moment, most of the algorithms are English-specific.

#### [franc](https://github.com/wooorm/franc) ([website](http://wooorm.com/franc/))

> Detect the language of text.

`franc` can tell in which of the 339 supported languages a piece of text is written.

#### [retext](https://github.com/wooorm/retext)

>  Natural language processor powered by plugins.

#### [lunr.js](https://github.com/olivernn/lunr.js) ([website](http://lunrjs.com/))

> Simple full-text search in your browser

Since lunr.js only supports English by default, supplement it with [lunr-languages](https://github.com/MihaiValentin/lunr-languages) which is a collection of languages stemmers and stopwords.

#### [nlp_compromise](https://github.com/nlp-compromise/nlp_compromise) 

> It's a handy, and not overly-fancy tool for understanding, changing, and playing with English.

#### [snowball-js](https://github.com/fortnightlabs/snowball-js)

> javascript implementation of the popular snowball word stemming nlp algorithm

## Data sets

### Language

#### [Words](https://github.com/atebits/Words/) 

> A _huge_ dataset of words in four languages (English, German, Spanish and French) used in Atebits' game Letterpress.

#### [corpora](https://github.com/dariusk/corpora) 

> A collection of small corpuses of interesting data for the creation of bots and similar stuff.

### Geographical Data

#### [Natural Earth Vector](https://github.com/nvkelso/natural-earth-vector) 

> A global, public domain map dataset available at three scales and featuring tightly integrated vector and raster data.

#### [countries](https://github.com/mledoze/countries) 

> World countries in JSON, CSV and XML.

#### [geonames](http://www.geonames.org/export/) 

> contains over 10 million geographical names and consists of over 9 million unique features whereof 2.8 million populated places and 5.5 million alternate names.

#### [Geofabrik OSM Data Extracts](http://download.geofabrik.de/) 

On continent/country level.

#### [Mapzen Metro Extracts](https://mapzen.com/data/metro-extracts) 

> City-sized portions of OpenStreetMap, served weekly 

#### [all-the-cities](https://github.com/zeke/all-the-cities) 

> All the 138,398 cities of the world with a population of at least 1000 inhabitants, in a big JSON array.

### Miscellaneous datasets

#### [Awesome public datasets](https://github.com/caesar0301/awesome-public-datasets)

#### [whiskyverse](https://github.com/Jonty/whiskyverse/) 

> JSON file containing Scotch Malt Whisky Society bottles


## APIs

#### [Wordnik](http://developer.wordnik.com/) 

> The Wordnik API lets you request definitions, example sentences, spelling suggestions, related words like synonyms and antonyms, phrases containing a given word, word autocompletion, random words, words of the day, and much more.

#### [poetrydb](https://github.com/thundercomb/poetrydb) ([website](http://poetrydb.org))

> PoetryDB is an API for internet poets.

#### [Echo Nest](http://developer.echonest.com/) 

> The Echo Nest offers an incredible array of music data and services for developers to build amazing apps and experiences. See also [echonest/remix](https://github.com/echonest/remix).

#### [Openapi](http://openapi.ro/) (Romanian 🇷🇴)

> Provides information about companies, IP geolocation, validation for CIF / CNP / IBAN / BIC, exchange rate, postal codes, singular and plural forms of Romanian words


## Command-Line Tools

#### [fonttools](https://github.com/behdad/fonttools/)

Does TTF/OTF conversion to and from XML. This allows you to edit fonts (e.g. metadata) in plain-text and then rebuild them.

#### [Osmosis](http://wiki.openstreetmap.org/wiki/Osmosis) 

Helps you filter & merge OpenStreetMap data files (XML, PBF).

#### [textkit](https://github.com/learntextvis/textkit) 

> Command line tool for manipulating and analyzing text 

#### [electron-pdf](https://github.com/fraserxu/electron-pdf) 

> A command line tool to generate PDF from URL, HTML or Markdown files. 

#### [unproject_text](https://github.com/mzucker/unproject_text) ([article](https://mzucker.github.io/2016/10/11/unprojecting-text-with-ellipses.html))

> Perspective recovery of text using transformed ellipses.

A Python script to adjust the perspective for scanned/photographed pages of texts, making it easier to run Optical Character Recognition on it.

#### [page_dewarp](https://github.com/mzucker/page_dewarp) ([article](https://mzucker.github.io/2016/08/15/page-dewarping.html))

> Page dewarping and thresholding using a "cubic sheet" model.

#### [pup](https://github.com/ericchiang/pup)

> pup is a command line tool for processing HTML. It reads from stdin, prints to stdout, and allows the user to filter parts of the page using CSS selectors.

Should work great with `wget` for web page data extraction.

## Online tools

#### [geojson.io](http://geojson.io) 

> geojson.io is a quick, simple tool for creating, viewing, and sharing maps. geojson.io is named after GeoJSON, an open source data format, and it supports GeoJSON in all ways - but also accepts KML, GPX, CSV, GTFS, TopoJSON, and other formats.

#### [Overpass Turbo](https://overpass-turbo.eu/) 

> A web-based data filtering tool for OpenStreetMap. With overpass turbo you can run Overpass API queries and analyse the resulting OSM data interactively on a map. There is an integrated Wizard which makes creating queries super easy.

---

## Miscellaneous tips & tricks

### Start a server for a folder

Run `python -m SimpleHTTPServer` in your project folder to make it available at [`http://localhost:8000`](http://localhost:8000).

__Note:__ The syntax above is for the Python 2.x that comes preinstalled with macOS and Linux. The equivalent syntax for Python 3 is `python -m http.server`. 

### Fetch a file from the web

To fetch a file from the web with the command line, using `wget` is straightforward:

```shell
wget http://download.geofabrik.de/europe/romania-latest.osm.pbf
```

(On macOS, you can install `wget` with Homebrew: `brew install wget`)

Or, fetching a file in Node.js:

```js
require('http').get('http://download.geofabrik.de/europe/romania-latest.osm.pbf', function(response) {
    response.pipe(require('fs').createWriteStream('romania-latest.osm.pbf'));
});
```

### Make an S3 bucket publicly available

To use a S3 bucket to keep a bunch of files and make them publicly available, you need to make a __bucket policy__. This is under _Permissions_ section on the _Properties_ tab for your bucket. Paste this into the bucket policy (`myBucketName` should be the name of your bucket):

```js
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "PublicReadGetObject",
			"Effect": "Allow",
			"Principal": "*",
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::myBucketName/*"
		}
	]
}
```

All the files inside will typically be available at `http://myBucketName.s3.amazonaws.com/path/to/file` but you can grab the exact URL from the _Static Website Hosting_ section in the _Properties_ tab.

__Extra credit:__ This is super-useful for hosting video files, since S3 supports __partial content requests__ which is needed to loop `<video>` on your web pages.

### `wget` for website mirroring / scraping

Here are some useful tricks with `wget`. [More of them here](http://www.labnol.org/software/wget-command-examples/28750/).

#### Mirror a website

```
wget --mirror --no-clobber --no-parent --wait=3 --execute robots=off --domains=danburzo.ro,assets.danburzo.ro ‐‐user-agent=Mozilla danburzo.ro
```

A quick explanation for these flags: 

* `--mirror` is a shorthand for `-r -N -l inf --no-remove-listing`, which are some switches useful for scraping
* `--no-clobber` instructs wget not to fetch each occurrence of the same URL as a separate file
* `--no-parent` don't go up the hierarchy
* `--wait=seconds` is used to wait for N seconds between requests, a.k.a. being nice to the server
* `--execute robots=off` will ignore the `robots.txt` file on the website and any `nofollow` attributes on links
* `--domains=domain1,domain2,...` is a list of domain names to consider when crawling (you'll want to include here any domains that hold the assets for the page)
* `--user-agent=UserAgentString` can be used in case the server blocks access based on the User Agent

#### Download sequential URLs

```
wget http://example.com/records/{1..1000}
```

#### Download a list of URLs

The URLs can be specified in a separate file `list-of-URLs.txt`, with one URL per line.

```
wget ‐‐input list-of-URLs.txt
```

