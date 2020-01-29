# ImageMagick Recipes

_Note: these recipes use ImageMagick v7.0+_

See also: [ImageMagick command-line reference](https://imagemagick.org/script/command-line-processing.php)

## Recipes

### Crop an image to a certain aspect ratio

The command below crops an image to a square by shaving off the excess from the long side:

```bash
magick my_image.jpg -gravity Center -crop 1:1 my_image_cropped.jpg
```

The order of the arguments here matters — think of it as a sort of pipeline:

* `-gravity Center` sets the origin of the crop (by default, pixels are shaved off of the bottom / right-hand side of the image)
* `-crop 1:1` crops the image to an aspect ratio of `1:1` (square)

To crop a whole set of images in bulk, we use a modified command:

```bash
mkdir -p cropped && \
magick './*.jpg' \
	-set filename:name "%t" \
	-gravity Center \
	-crop 1:1 \
	"cropped/%[filename:name].jpg"
```

The command above makes a cropped copy of each JPEG image in the current folder and places it with its original name under a `cropped` subfolder.

Some key parts:

* `mkdir -p cropped` creates the `cropped` folder if it doesn't already exist (via the `-p` flag); we need it to exist prior to running the `magick` command, otherwise we'll get an error;
* `-set filename:name "%t"` — we need this bit so that the image's original filename becomes available for interpolation in the output filename; notice we then use it as `"cropped/%[filename:name].jpg"`; (for some reason, we can't use `%t` directly in the output file name...)

The command is not particularly fast, and it takes a while for _any_ output to show up. For 600-ish images around 2000x2000px, it took about 20 minutes on my machine, and output began at about the 12 minute mark. For more incremental output, we can go through each image in the folder in Bash rather than ImageMagick:

```bash
mkdir -p cropped && \
for i in *.jpg; do \
	magick $i \
		-set filename:name "%t" \
		-gravity Center \
		-crop 1:1 \
	"cropped/%[filename:name].jpg"; \
done
```

This will run the crop command on an image at a time, so you'll notice the `cropped` sub-folder fill up steadily.
