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
	* [App Architecture](#app-architecture)
	* [Prototyping](#prototyping)
	* [Web scraping, data extraction](#web-scraping-data-extraction)
	* [Language processing](#language-processing)
	* [Machine Learning](#machine-learning)
	* [Parsing things](#parsing-things)
	* [Building CLIs](#building-clis)
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
* [Cheatsheets & recipes](#cheatsheets--recipes)
	* [`ffmpeg`](#ffmpeg)
	* [`wget`](#wget)
	* [Unix command-line tools](#unix-command-line-tools)
	* [MySQL queries](#mysql-queries)
	* [Adobe Products](#adobe)
* [Other lists](#other-lists)

## JavaScript libraries

(The ★ star denotes popular, high-quality, choices.)

### Image processing, optical character recognition (OCR)

Repo | Description | Notes
---- | ----------- | -----
[quaggaJS](https://github.com/serratus/quaggaJS) | QuaggaJS is a barcode-scanner entirely written in JavaScript supporting real-time localization and decoding of various types of barcodes such as EAN, CODE 128, CODE 39, EAN 8, UPC-A, UPC-C, I2of5 and CODABAR. The library is also capable of using `getUserMedia` to get direct access to the user's camera stream. Although the code relies on heavy image- processing even recent smartphones are capable of locating and decoding barcodes in real-time. | For reading barcodes with a webcam or phone camera. See also [JSBarcode](https://github.com/lindell/JsBarcode) for _generating_ barcodes.
[omggif](https://github.com/deanm/omggif) | JavaScript implementation of a GIF 89a encoder and decoder. | For making GIFs. [Animated_GIF](https://github.com/sole/Animated_GIF), for example, builds on top of this library.
[exif.js](https://github.com/jseidelin/exif-js) | JavaScript library for reading EXIF image metadata. | Extracting information from JPEG files.
[Lanczos.js](https://github.com/mudcube/Lanczos.js) | Lancszos image resampling. | This is for resizing images nicely in the browser.
[tesseract.js](https://github.com/naptha/tesseract.js) | Tesseract.js is a javascript library that gets words in almost any language out of images. | 
[sharp](https://github.com/lovell/sharp) [↪](http://sharp.dimens.io) | High performance Node.js image processing, the fastest module to resize JPEG, PNG, WebP and TIFF images. Uses the libvips library. |

### Drawing, illustration, motion

Repo | Description | Notes
---- | ----------- | -----
★ [chroma.js](https://github.com/gka/chroma.js) | JavaScript library for all kinds of color manipulations. | Convert a color from and to any format, generate pleasing color palettes and color variations. See also [TinyColor](https://github.com/bgrins/TinyColor), [d3-color](https://github.com/d3/d3-color) and my own [culori](https://github.com/danburzo/culori).
★ [p5.js](https://github.com/lmccart/p5.js) | A JS client-side library for creating graphic and interactive experiences, based on the core principles of Processing. | 
★ [paper.js](https://github.com/paperjs/paper.js) | The Swiss Army Knife of Vector Graphics Scripting. |
★ [opentype.js](https://github.com/nodebox/opentype.js) | Read and write OpenType fonts using JavaScript. | 
[two.js](https://github.com/jonobr1/two.js) | A renderer-agnostic two-dimensional drawing API for the web. |
[snap.svg](https://github.com/adobe-webplatform/Snap.svg) | The JavaScript library for modern SVG graphics. |
[rune.js](https://github.com/runemadsen/rune.js) | A JavaScript library for programming graphic design systems with SVG. | 
[mojs](https://github.com/legomushroom/mojs) | motion graphics toolbelt for the web | 
[matter-js](https://github.com/liabru/matter-js) | A 2D rigid body physics engine for the web |
[ccapture.js](https://github.com/spite/ccapture.js/) | A library to capture canvas-based animations at a fixed framerate. |

### Data visualization

Repo | Description | Notes
---- | ----------- | -----
★ [d3](https://github.com/mbostock/d3) | A JavaScript visualization library for HTML and SVG. | The tool of choice for any data visualization project. To draw standard charts with D3, take a look at some libraries built on top of it: [MetricsGraphics](https://github.com/mozilla/metrics-graphics), [plottable](https://github.com/palantir/plottable), [d3plus](https://github.com/alexandersimoes/d3plus), [victory](https://github.com/FormidableLabs/victory), [semiotic](https://github.com/emeeks/semiotic). __Further reading:__ [awesome-d3](https://github.com/wbkd/awesome-d3).
[vega-lite](https://github.com/vega/vega-lite) [↪](https://vega.github.io/vega-lite/) | Vega-Lite is a high-level grammar of interactive graphics. It provides a concise JSON syntax for rapidly generating visualizations to support analysis. |
[cytoscape.js](https://github.com/cytoscape/cytoscape.js) [↪](http://js.cytoscape.org/) | Graph theory (a.k.a. network) library for analysis and visualisation. | 
[dagre](https://github.com/cpettitt/dagre) | Directed graph renderer for JavaScript | Built on top of [graphlib](https://github.com/cpettitt/graphlib) by the same author, `dagre` helps you build directed graphs that you can then plug into D3 or cytoscape. See [the excellent wiki](https://github.com/cpettitt/dagre/wiki) for details.

### 3D, VR, WebGL

Repo | Description | Notes
---- | ----------- | -----
★ [three.js](https://github.com/mrdoob/three.js/) [↪](https://threejs.org/) | JavaScript 3D library. | Much like D3 is the tool of choice for data visualization, three.js is the established library for working in 3D. See also [pre3d](https://github.com/deanm/pre3d/) (although it hasn't been worked on in ages).
[regl](https://github.com/mikolalysenko/regl) [↪](http://regl.party/) | Fast functional WebGL. |
[cannon.js](https://github.com/schteppe/cannon.js) | Inspired by three.js and ammo.js, and driven by the fact that the web lacks a physics engine, here comes cannon.js. The rigid body physics engine includes simple collision detection, various body shapes, contacts, friction and constraints. |
[aframe](https://github.com/aframevr/aframe/) [↪](https://aframe.io/) | Building blocks for the VR Web. |
[blotter](https://github.com/bradley/Blotter) [↪](https://blotter.js.org) | A JavaScript API for drawing unconventional text effects on the web. | It uses three.js under the hood.
[pex](https://github.com/pex-gl/pex) [↪](http://variable.io/pex/) | PEX is a collection of modular software components that work together well to create a tool for computation thinking. |
[ejecta](https://github.com/phoboslab/ejecta)  | A Fast, Open Source JavaScript, Canvas & Audio Implementation for iOS | Can help you bring things built with three.js, etc. to iOS.

### Audio

Repo | Description | Notes
---- | ----------- | -----
★ [Tone.js](https://github.com/Tonejs/Tone.js) | A Web Audio framework for making interactive music in the browser. |
[paulstretch.js](https://github.com/sebpiq/paulstretch.js) | This is a JavaScript implementation - with a few improvements - of Paul's Extreme Sound Stretch algorithm (Paulstretch) by Nasca Octavian PAUL. |
[tuna](https://github.com/Dinahmoe/tuna)  | An audio effects library for Web Audio. |
[MIDI.js](https://github.com/mudcube/MIDI.js) | Making life easy to create a MIDI-app on the web. |
[teoria](https://github.com/saebekassebil/teoria) | Javascript taught Music Theory |
[WebMidi.js](https://github.com/cotejp/webmidi) | WebMidi.js helps you tame the Web MIDI API. Send and receive MIDI messages with ease. Control instruments with user-friendly functions (playNote, sendPitchBend, etc.). React to MIDI input with simple event listeners (noteon, pitchbend, controlchange, etc.) |
[NexusUI](https://github.com/lsu-emdm/nexusUI) [↪](http://www.nexusosc.com/) | NexusUI is a JavaScript toolkit for easily designing musical interfaces in web browsers and mobile apps, with emphasis on rapid prototyping and integration with web audio. |
[Gibberish](https://github.com/charlieroberts/Gibberish) [↪](http://www.charlie-roberts.com/gibberish/) | Fast, JavaScript DSP library that creates JIT optimized audio callbacks using code generation techniques | Library behind [Gibber](https://github.com/charlieroberts/Gibber) [↪](http://gibber.mat.ucsb.edu/) &mdash; an audiovisual live coding environment for the browser. See also [interface.js](https://github.com/charlieroberts/interface.js) [↪](http://www.charlie-roberts.com/interface/) by the same author &mdash; a GUI library for music / arts applications that works with touch, mouse and motion events. 
[genish.js](https://github.com/charlieroberts/genish.js) [↪](http://www.charlie-roberts.com/genish/) | A library for generating optimized, single-sample audio callbacks in JavaScript. Inspired by gen~ in Max/MSP. |
[howler.js](https://github.com/goldfire/howler.js) [↪](https://howlerjs.com/) | howler.js is an audio library for the modern web. It defaults to Web Audio API and falls back to HTML5 Audio. This makes working with audio in JavaScript easy and reliable across all platforms. |

#### Utilities

Repo | Description | Notes
---- | ----------- | -----
[StartAudioContext](https://github.com/tambien/StartAudioContext) | starts the Web Audio API's AudioContext on an explicit user action. |
[MediaStreamRecorder](https://github.com/streamproc/MediaStreamRecorder) [↪](https://www.webrtc-experiment.com/msr/) | Cross-browser audio/video/screen recording. It supports Chrome, Firefox, Opera and Microsoft Edge. It even works on Android browsers. It follows latest MediaRecorder API standards and provides similar APIs. |

#### Dig deeper

* [awesome-webaudio](https://github.com/notthetup/awesome-webaudio)
* [web-audio-resources](https://github.com/alemangui/web-audio-resources)

### User Interfaces

Repo | Description | Notes
---- | ----------- | -----
[zingtouch](https://github.com/zingchart/zingtouch) | A JavaScript touch gesture detection library for the modern web |
[shake.js](https://github.com/alexgibson/shake.js/) [↪](https://alexgibson.github.io/shake.js/) | A custom 'shake' event plugin for mobile web browsers using device accelerometer. 

### Mapping

Repo | Description | Notes
---- | ----------- | -----
★ [leaflet.js](https://github.com/Leaflet/Leaflet) | JavaScript library for mobile-friendly interactive maps. |
[Stamen maps](https://github.com/stamen/maps.stamen.com) | This is the code behind the Stamen maps site, which shows off our custom tiles and explains how to get them into other sites. |
[turf.js](https://github.com/Turfjs/turf) | A modular geospatial engine written in JavaScript.

### Gamemaking

Repo | Description | Notes
---- | ----------- | -----
[coquette](https://github.com/maryrosecook/coquette)  | A micro framework for JavaScript games. Handles collision detection, the game update loop, canvas rendering, and keyboard and mouse input. |

### Working with documents

Repo | Description | Notes
---- | ----------- | -----
[pdf.js](https://github.com/mozilla/pdf.js/) | PDF reader in JavaScript. |
[pdf2json](https://github.com/modesty/pdf2json) | A PDF file parser that converts PDF binaries to text-based JSON, powered by a fork of pdf.js |
[pdfkit](https://github.com/devongovett/pdfkit) | A JavaScript PDF generation library for Node and the browser |
[jsPDF](https://github.com/MrRio/jsPDF) | Generate PDF files in JavaScript. |
[epub.js](https://github.com/futurepress/epub.js/) | EPUBs in the browser. |
[magicbook](https://github.com/magicbookproject/magicbook) | It aims to be the best free tool for creating print and digital books from a single source. |

### Algorithms, Data structures

Repo | Description | Notes
---- | ----------- | -----
[mnemonist](https://github.com/Yomguithereal/mnemonist) | Curated collection of data structures for the JavaScript language. |
[graphlib](https://github.com/cpettitt/graphlib) | A directed multi-graph library for JavaScript. |

### App architecture

Repo | Description | Notes
---- | ----------- | -----
★ [react](https://github.com/facebook/react) [↪](https://reactjs.org/) | A declarative, efficient, and flexible JavaScript library for building user interfaces. | 
[vue](https://github.com/vuejs/vue) [↪](http://vuejs.org/) | Simple yet powerful library for building modern web interfaces. | A lightweight alternative to React.
[Bluebird](https://github.com/petkaantonov/bluebird) | Bluebird is a full featured promise library with unmatched performance. |

### Prototyping

This section contains tools that make it easier to just start working on your thing without a lot of setup.

Repo | Description | Notes
---- | ----------- | -----
[storybook](https://github.com/storybooks/storybook) [↪](https://storybook.js.org/) | Storybook is a development environment for UI components. It allows you to browse a component library, view the different states of each component, and interactively develop and test components. | This works as a React (or Vue) playground that lets you focus on writing components.
[hackathon-starter](https://github.com/sahat/hackathon-starter) | A boilerplate for Node.js web applications |

### Web scraping, data extraction

Repo | Description | Notes
---- | ----------- | -----
[artoo](https://github.com/medialab/artoo) | artoo.js is a piece of JavaScript code meant to be run in your browser's console to provide you with some scraping utilities. | Allows you to create custom bookmarklets to scrape a web page from your browser; I could see this being used in places where on a server you'd have to jump through some hoops, e.g. getting your Facebook saved links.
[x-ray](https://github.com/lapwinglabs/x-ray) | The next web scraper. See through the `<html>` noise. | From the maker of [cheerio](https://github.com/cheeriojs/cheerio), and built on top of it, x-ray gives you a terse, fluent API to scrape and navigate pages.
[fathom](https://github.com/mozilla/fathom) | A framework for extracting meaning from web pages. | Seems to be still a work in progress, but it will ultimately be a tool for understanding where some particular type of content is on a page: _"Where is the body? The title? Is this a 'next page' button? Is this a comment form, and are there comments here? By better understanding the parts of a page, we can improve our understanding of how a user interacts with it."_ — [source](https://wiki.mozilla.org/Context_Graph#Fathom)
[readability](https://github.com/mozilla/readability) | A standalone version of the readability library used for Firefox Reader View. | Extract the main content from a web page.

### Language processing

Repo | Description | Notes
---- | ----------- | -----
[natural](https://github.com/NaturalNode/natural) | "Natural" is a general natural language facility for nodejs. Tokenizing, stemming, classification, phonetics, tf-idf, WordNet, string similarity, and some inflections are currently supported. At the moment, most of the algorithms are English-specific. |
[franc](https://github.com/wooorm/franc) [↪](http://wooorm.com/franc/) | Detect the language of text. |`franc` can tell in which of the 339 supported languages a piece of text is written.
[retext](https://github.com/wooorm/retext) | Natural language processor powered by plugins. | 
[lunr.js](https://github.com/olivernn/lunr.js) [↪](http://lunrjs.com/) | Simple full-text search in your browser | Since lunr.js only supports English by default, supplement it with [lunr-languages](https://github.com/MihaiValentin/lunr-languages) which is a collection of languages stemmers and stopwords.
[nlp_compromise](https://github.com/nlp-compromise/nlp_compromise) | It's a handy, and not overly-fancy tool for understanding, changing, and playing with English. |
[snowball-js](https://github.com/fortnightlabs/snowball-js) | javascript implementation of the popular snowball word stemming nlp algorithm | 

### Machine Learning

Repo | Description | Notes
---- | ----------- | -----
[deeplearn.js](https://github.com/PAIR-code/deeplearnjs) [↪](https://deeplearnjs.org/) |Hardware-accelerated deep learning // machine learning // NumPy library for the web. |

### Parsing things

Repo | Description | Notes
---- | ----------- | -----
[parse5](https://github.com/inikulin/parse5) | parse5 provides nearly everything you may need when dealing with HTML. It's the fastest spec-compliant HTML parser for Node to date. It parses HTML the way the latest version of your browser does. | Use this to get a barebones representation of your HTML
★ [jsdom](https://github.com/jsdom/jsdom) | jsdom is a pure-JavaScript implementation of many web standards, notably the WHATWG DOM and HTML Standards, for use with Node.js. | Use this for more convenient methods to interact with the HTML (e.g. `querySelectorAll()`)
[css](https://github.com/reworkcss/css) | CSS parser / stringifier for Node.js |
[postcss](https://github.com/postcss/postcss) | PostCSS is a tool for transforming styles with JS plugins. These plugins can lint your CSS, support variables and mixins, transpile future CSS syntax, inline images, and more. | 
[acorn](https://github.com/acornjs/acorn) | A tiny, fast JavaScript parser, written completely in JavaScript. | 
[@babel/parser](https://github.com/babel/babel/tree/master/packages/babel-parser) [↪](https://babeljs.io/docs/en/next/babel-parser.html) | The Babel parser (previously Babylon) is a JavaScript parser used in Babel. | 
[recast](https://github.com/benjamn/recast) | JavaScript syntax tree transformer, nondestructive pretty-printer, and automatic source map generator. | Uses [`esprima`](https://github.com/jquery/esprima)\* as the default parser, but can be configured for `acorn` or `@babel/parser`. 

<small>\* `esprima` is one of the more mature ECMAScript parsers.</small>

### Building CLIs

Repo | Description | Notes
---- | ----------- | -----
[commander.js](https://github.com/tj/commander.js) | node.js command-line interfaces made easy | 

## Data sets

### Language

Repo | Description | Notes
---- | ----------- | -----
[Words](https://github.com/atebits/Words/) | A _huge_ dataset of words in four languages (English, German, Spanish and French) used in Atebits' game Letterpress. |
[corpora](https://github.com/dariusk/corpora) | A collection of small corpuses of interesting data for the creation of bots and similar stuff. | I also keep a repo, [inspired by it](https://github.com/danburzo/corpora).

### Geographical Data

Link | Description | Notes
---- | ----------- | -----
[Natural Earth Vector](https://github.com/nvkelso/natural-earth-vector) | A global, public domain map dataset available at three scales and featuring tightly integrated vector and raster data. |
[countries](https://github.com/mledoze/countries) | World countries in JSON, CSV and XML. |
[geonames](http://www.geonames.org/export/) | contains over 10 million geographical names and consists of over 9 million unique features whereof 2.8 million populated places and 5.5 million alternate names. |
[Geofabrik OSM Data Extracts](http://download.geofabrik.de/) | | On continent/country level.
[Mapzen Metro Extracts](https://mapzen.com/data/metro-extracts) | City-sized portions of OpenStreetMap, served weekly | 
[all-the-cities](https://github.com/zeke/all-the-cities) | All the 138,398 cities of the world with a population of at least 1000 inhabitants, in a big JSON array. |

### Miscellaneous datasets

Link | Description | Notes
---- | ----------- | -----
[Awesome public datasets](https://github.com/caesar0301/awesome-public-datasets) | |
[whiskyverse](https://github.com/Jonty/whiskyverse/) | | JSON file containing Scotch Malt Whisky Society bottles

## APIs

Link | Description | Notes
---- | ----------- | -----
[Wordnik](http://developer.wordnik.com/) | The Wordnik API lets you request definitions, example sentences, spelling suggestions, related words like synonyms and antonyms, phrases containing a given word, word autocompletion, random words, words of the day, and much more. |
[poetrydb](https://github.com/thundercomb/poetrydb) [↪](http://poetrydb.org) | PoetryDB is an API for internet poets. |
[Echo Nest](http://developer.echonest.com/) | The Echo Nest offers an incredible array of music data and services for developers to build amazing apps and experiences. See also [echonest/remix](https://github.com/echonest/remix). |
[Openapi](http://openapi.ro/) 🇷🇴 | Provides information about companies, IP geolocation, validation for CIF / CNP / IBAN / BIC, exchange rate, postal codes, singular and plural forms of Romanian words |

## Command-Line Tools

Link | Description | Notes
---- | ----------- | -----
[fonttools](https://github.com/behdad/fonttools/) | | Does TTF/OTF conversion to and from XML. This allows you to edit fonts (e.g. metadata) in plain-text and then rebuild them.
[Osmosis](http://wiki.openstreetmap.org/wiki/Osmosis) | | Helps you filter & merge OpenStreetMap data files (XML, PBF).
[textkit](https://github.com/learntextvis/textkit) | Command line tool for manipulating and analyzing text |
[electron-pdf](https://github.com/fraserxu/electron-pdf) | A command line tool to generate PDF from URL, HTML or Markdown files. |
[unproject_text](https://github.com/mzucker/unproject_text) [article](https://mzucker.github.io/2016/10/11/unprojecting-text-with-ellipses.html) | Perspective recovery of text using transformed ellipses. | A Python script to adjust the perspective for scanned/photographed pages of texts, making it easier to run Optical Character Recognition on it.
[page_dewarp](https://github.com/mzucker/page_dewarp) [article](https://mzucker.github.io/2016/08/15/page-dewarping.html) | Page dewarping and thresholding using a "cubic sheet" model. |
[pup](https://github.com/ericchiang/pup) | pup is a command line tool for processing HTML. It reads from stdin, prints to stdout, and allows the user to filter parts of the page using CSS selectors. | Should work great with `wget` for web page data extraction.
RAISR | [Google Rapid and Accurate Image Super Resolution](https://arxiv.org/pdf/1606.01299.pdf) is a technique to use Machine Learning to upscale images. | There are a few implementations of the algorithm on GitHub: [movehand/raisr](https://github.com/movehand/raisr), [MKFMIKU/RAISR](https://github.com/MKFMIKU/RAISR)

---

## Online tools

### Places for your code

Link | Description | Notes
---- | ----------- | -----
★ [Observable](https://beta.observablehq.com) | Observable is a better way to code. Discover insights faster and communicate more effectively with interactive notebooks for data analysis, visualization, and exploration. | See [this introductory series](https://beta.observablehq.com/collection/introduction) to get up to speed.
[Glitch](https://glitch.com/) | Glitch is the friendly community where you'll build the app of your dreams. | 
[CodePen](https://codepen.io) | CodePen is a social development environment for front-end designers and developers. |
[jsComplete](https://jscomplete.com/repl/) | | This is the simplest way I found to write React code like you would in a notepad. You can't save your work, but it's perfect for quick sketching. It also loads the latest version of React (16.2.0 at the moment).
[JS Bin](https://jsbin.com) | | 
[JSFiddle](https://jsfiddle.net) | |

### Mapping

Link | Description | Notes
---- | ----------- | -----
[geojson.io](http://geojson.io) | geojson.io is a quick, simple tool for creating, viewing, and sharing maps. geojson.io is named after GeoJSON, an open source data format, and it supports GeoJSON in all ways - but also accepts KML, GPX, CSV, GTFS, TopoJSON, and other formats. |
[Overpass Turbo](https://overpass-turbo.eu/) | A web-based data filtering tool for OpenStreetMap. With overpass turbo you can run Overpass API queries and analyse the resulting OSM data interactively on a map. There is an integrated Wizard which makes creating queries super easy. |

---

## Miscellaneous tips & tricks

### Start a server for a folder

Run `python -m SimpleHTTPServer` in your project folder to make it available at [`http://localhost:8000`](http://localhost:8000).

__Note:__ The syntax above is for the Python 2.x that comes preinstalled with macOS and Linux. The equivalent syntax for Python 3 is `python -m http.server`. 

If you're using Node.js, you can also use the [`serve`](https://npmjs.com/package/serve) package, which you can run without installing with [`npx`](https://www.npmjs.com/package/npx) (it comes with recent versions of `npm`):

```bash
npx serve
```

### Fetch a file from the web

To fetch a file from the web with the command line, using `wget` is straightforward:

```shell
wget http://download.geofabrik.de/europe/romania-latest.osm.pbf
```

> 👉 See [more `wget` tricks](./wget.md)

Or, fetching a file in Node:

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

## Cheatsheets & recipes

### `ffmpeg`

[See the list of recipes](./ffmpeg.md)

### `wget`

[See the list of recipes](./wget.md)

### Unix command-line tools

> The standard command-line tools available on Unix-based systems are wonderful, if occasionally inscrutable. This page contains some commands I found useful.

[See the list of recipes](./unix-cli.md)

### MySQL Queries

> Some useful tricks for working with data from MySQL tables.

[See the list of recipes](./mysql.md)

### Adobe products

[See the list of recipes](./adobe.md)

## Other lists

* [A few good open-source typefaces](./typefaces.md)

## Further reading

* [awesome-creative-coding](https://github.com/terkelg/awesome-creative-coding)
