# Toolbox

This is a collection of tricks, tools, libraries, APIs and data sources for creative projects. It's a reference as well as a compendium of things you can do in the browser and the command line.

It's insipired by [javierarce/toolbox](https://github.com/javierarce/toolbox). Contributions are welcome via [issues](https://github.com/danburzo/toolbox/issues) or [pull requests](https://github.com/danburzo/toolbox/pulls).

## JavaScript libraries

### Image processing

| Github repo | Description | Useful for |
| ----------- | ----------- | ---------- | 
[quaggaJS](https://github.com/serratus/quaggaJS) | An advanced barcode-scanner written in JavaScript. | Reading real-life barcodes with a webcam or phone camera. See [JSBarcode](https://github.com/lindell/JsBarcode) for _generating_ barcodes.
[omggif](https://github.com/deanm/omggif) | JavaScript implementation of a GIF 89a encoder and decoder. | Making GIFs. [Animated_GIF](https://github.com/sole/Animated_GIF), for example, builds on this.
[exif.js](https://github.com/jseidelin/exif-js) | JavaScript library for reading EXIF image metadata. | Extracting information from JPEG files |
[Lanczos.js](https://github.com/mudcube/Lanczos.js) | Lancszos image resampling. | Scaling images nicely |

### Drawing, illustration, motion

| Github repo | Description | Useful for |
| ----------- | ----------- | ---------- |
[chroma.js](https://github.com/gka/chroma.js) | JavaScript library for all kinds of color manipulations. | Converting a color from and to any format, generate pleasing color palettes and color variations. See also [TinyColor](https://github.com/bgrins/TinyColor).
[paper.js](https://github.com/paperjs/paper.js) | The Swiss Army Knife of Vector Graphics Scripting.
[two.js](https://github.com/jonobr1/two.js) | A renderer agnostic two-dimensional drawing api for the web.
[opentype.js](https://github.com/nodebox/opentype.js) | Read and write OpenType fonts using JavaScript.
[snap.svg](https://github.com/adobe-webplatform/Snap.svg) | The JavaScript library for modern SVG graphics.
[p5.js](https://github.com/lmccart/p5.js) | A JS client-side library for creating graphic and interactive experiences, based on the core principles of Processing.
[rune.js](https://github.com/runemadsen/rune.js) | A JavaScript library for programming graphic design systems with SVG.
[mojs](https://github.com/legomushroom/mojs) | motion graphics toolbelt for the web

### Data visualization

| Github repo | Description |
| ----------- | ----------- |
[d3](https://github.com/mbostock/d3) | A JavaScript visualization library for HTML and SVG.
[MetricsGraphics](https://github.com/mozilla/metrics-graphics) | A library optimized for concise, principled data graphics and layouts.
[dagre](https://github.com/cpettitt/dagre) | Directed graph renderer for JavaScript (see also [dagre-d3](https://github.com/cpettitt/dagre-d3)).
[WebCola](https://github.com/tgdwyer/WebCola) | JavaScript constraint-based graph layout.

### 3D, Virtual Reality

| Github repo | Description |
| ----------- | ----------- |
[three.js](https://github.com/mrdoob/three.js/) | JavaScript 3D library.
[pre3d](https://github.com/deanm/pre3d/) | JavaScript 3d rendering engine.
[aframe](https://aframe.io/) | Building blocks for the VR Web.

### Audio

| Github repo | Description |
| ----------- | ----------- |
[dancer.js](https://github.com/jsantell/dancer.js) |
[timbre.js](https://github.com/mohayonao/timbre.js/) | JavaScript library for objective sound programming 
[audio-tags](https://github.com/sole/audio-tags) | An experimental thingie bridging Web Components with Web Audio.
[MIDI.js](https://github.com/mudcube/MIDI.js) | Making life easy to create a MIDI-app on the web.
[tuna](https://github.com/Dinahmoe/tuna) | An audio effects library for Web Audio.
[PitchDetect](https://github.com/cwilso/PitchDetect) | Pitch detection in Web Audio using autocorrelation.
[WebAudio](https://github.com/cwilso/WebAudio) | Web Audio API Playground.
[Gibberish](https://github.com/charlieroberts/Gibberish) | Fast, JavaScript DSP library that creates JIT optimized audio callbacks using code generation techniques
[Tone.js](https://github.com/Tonejs/Tone.js) | A Web Audio framework for making interactive music in the browser. 
[howler.js](https://github.com/goldfire/howler.js) | Javascript audio library for the modern web.
[genish.js](https://github.com/charlieroberts/genish.js) | A library for generating optimized, single-sample audio callbacks in JavaScript. Inspired by gen~ in Max/MSP.

# User Interfaces

| Github repo | Description |
| ----------- | ----------- |
[interface.js](https://github.com/charlieroberts/interface.js) | gui library for music / arts applications that works with touch, mouse and motion events.
[Gibber](https://github.com/charlieroberts/Gibber) | An audiovisual live coding environment for the browser.

### Mapping

| Github repo | Description |
| ----------- | ----------- |
[leaflet.js](https://github.com/Leaflet/Leaflet) | JavaScript library for mobile-friendly interactive maps.
[Stamen maps](https://github.com/stamen/maps.stamen.com) | 
[turf.js](https://github.com/Turfjs/turf) | A modular geospatial engine written in JavaScript.

### Gamemaking

| Github repo | Description |
| ----------- | ----------- |
[coquette](https://github.com/maryrosecook/coquette) | A micro framework for JavaScript games. Handles collision detection, the game update loop, canvas rendering, and keyboard and mouse input.

### Rich text editing

| Github repo | Description |
| ----------- | ----------- |
[scribe](https://github.com/guardian/scribe) | A rich text editor framework for the web platform.

### Working with documents

| Github repo | Description |
| ----------- | ----------- |
[pdf.js](https://github.com/mozilla/pdf.js/) | PDF reader in JavaScript.
[pdf2json](https://github.com/modesty/pdf2json) | A PDF file parser that converts PDF binaries to text-based JSON, powered by a fork of pdf.js
[pdfkit](https://github.com/devongovett/pdfkit) | A JavaScript PDF generation library for Node and the browser
[jsPDF](https://github.com/MrRio/jsPDF) | Generate PDF files in JavaScript. 
[epub.js](https://github.com/futurepress/epub.js/) | EPUBs in the browser.
[magicbook](https://github.com/magicbookproject/magicbook) | It aims to be the best free tool for creating print and digital books from a single source.

### Algorithms, Data structures

| Github repo | Description |
| ----------- | ----------- |
[graphlib](https://github.com/cpettitt/graphlib) | A directed multi-graph library for JavaScript.
[brain](https://github.com/harthur/brain) | Neural networks in JavaScript.

### Sensible app architecture

| Github repo | Description |
| ----------- | ----------- |
[Backbone](https://github.com/jashkenas/backbone) | Models, Views, Collections, Events, Router.
[Ractive](https://github.com/ractivejs/ractive) | Next-generation DOM manipulation.
[Bluebird](https://github.com/petkaantonov/bluebird) | Bluebird is a full featured promise library with unmatched performance.
[hackathon-starter](https://github.com/sahat/hackathon-starter) | A boilerplate for Node.js web applications

### Web scraping

| Github repo | Description |
| ----------- | ----------- |
[artoo](https://github.com/medialab/artoo) | is a client-side scraper; you enable it on a page via a bookmarklet to quickly prototype scrapers in the console -- you can also make your own custom bookmarklets via Gulp.
[fathom](https://github.com/mozilla/fathom) | A framework for extracting meaning from web pages.

## Data sets

### Language

| Github repo | Description |
| ----------- | ----------- |
[Words](https://github.com/atebits/Words/) | A _huge_ dataset of words in four languages (English, German, Spanish and French) used in Atebits' game Letterpress.
[corpora](https://github.com/dariusk/corpora) | A collection of small corpuses of interesting data for the creation of bots and similar stuff.

### Geographical Data

| Name | Description |
| ---- | ----------- |
[Natural Earth Vector](https://github.com/nvkelso/natural-earth-vector) | A global, public domain map dataset available at three scales and featuring tightly integrated vector and raster data.
[countries](https://github.com/mledoze/countries) | World countries in JSON, CSV and XML.
[geonames](http://www.geonames.org/export/) | contains over 10 million geographical names and consists of over 9 million unique features whereof 2.8 million populated places and 5.5 million alternate names.
[Geofabrik OSM Data Extracts](http://download.geofabrik.de/) | on continent/country level.
[Mapzen Metro Extracts](https://mapzen.com/data/metro-extracts) | City-sized portions of OpenStreetMap, served weekly 

### Lists of datasets

| Github repo | Description |
| ----------- | ----------- |
[Awesome public datasets](https://github.com/caesar0301/awesome-public-datasets) | 


## APIs

| Name | Description |
| ---- | ----------- |
[Wordnik](http://developer.wordnik.com/) | The Wordnik API lets you request definitions, example sentences, spelling suggestions, related words like synonyms and antonyms, phrases containing a given word, word autocompletion, random words, words of the day, and much more.
[Echo Nest](http://developer.echonest.com/) | The Echo Nest offers an incredible array of music data and services for developers to build amazing apps and experiences. See also [echonest/remix](https://github.com/echonest/remix).

## Command-Line Tools

| Name | Description |
| ---- | ----------- |
[fonttools](https://github.com/behdad/fonttools/) | does TTF/OTF conversion to and from XML. This allows you to edit fonts (e.g. metadata) in plain-text and then rebuild them.
[Osmosis](http://wiki.openstreetmap.org/wiki/Osmosis) | helps you filter & merge OpenStreetMap data files (XML, PBF).

## Online tools

| Name | Description |
| ---- | ----------- |
[geojson.io](http://geojson.io) | geojson.io is a quick, simple tool for creating, viewing, and sharing maps. geojson.io is named after GeoJSON, an open source data format, and it supports GeoJSON in all ways - but also accepts KML, GPX, CSV, GTFS, TopoJSON, and other formats.
[Overpass Turbo](https://overpass-turbo.eu/) | a web-based data filtering tool for OpenStreetMap. With overpass turbo you can run Overpass API queries and analyse the resulting OSM data interactively on a map. There is an integrated Wizard which makes creating queries super easy.

---

## Miscellaneous tips & tricks

#### Start a server for a folder

OS X and Linux come with Python preinstalled. In your project folder, run `python -m SimpleHTTPServer`. This makes it available at [`http://localhost:8000`](http://localhost:8000).

#### Fetch a file from the web

If you want to get a data file from the web in the command line, `wget` is the simplest:

```shell
wget http://download.geofabrik.de/europe/romania-latest.osm.pbf
```

(On OS X, you can install `wget` with Homebrew: `brew install wget`)

To fetch a file using Node, a minimal example:

```js
var http = require('http');
var fs = require('fs');

var url = 'http://download.geofabrik.de/europe/romania-latest.osm.pbf';
var output = 'romania-latest.osm.pbf';

http.get(url, function(res) {
	res.pipe(fs.createWriteStream(output));
});
```

#### Make a S3 bucket publicly available

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

This is super-useful for hosting video files, since S3 supports __partial content requests__ which is needed to loop `<video>` on your web pages.

### Quick project scaffolding

In the command line, you can use the `mkdir` and `touch` utilities to quickly create a bunch of folders and files for your project:

```
cd my-project
mkdir js css img test
touch .gitignore index.html README.md CHANGELOG.md css/style.css js/app.js
```

This will create the structure:

```
- my-project
  - css
    - style.css
  - js
    - app.js
  - img
  - test
  .gitignore
  index.html
  README.md
  CHANGELOG.md
```

