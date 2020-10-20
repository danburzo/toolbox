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
for img in *.jpg; do magick $img -gravity Center -crop 1:1 "cropped/$img.jpg"; done
```

This will run the crop command on an image at a time, so you'll notice the `cropped` sub-folder fill up steadily. Using Bash we can avoid the `-set` parameter and just use our `$img` identifier.

### Resize an image to fit a certain size

In the example below, we resize an image so that it fits within a 1000px &times; 1000px box, while maintaining its aspect ratio (analogous to using `object-fit: contain` in CSS):

```bash
magick my_image.jpg \
	-gamma .45455 \
	-resize 1000x1000 \
	-unsharp 1.8x1.3+0.4+0 \
	-gamma 2.2 \
	my_image_resized.jpg
```

We use the `-gamma` option to decode the image to linear encoding, and then change it back to 2.2 after the resize — this is mentioned in the ImageMagick docs for `-resize`, but I'm not sure why it's necessary.

After resize we sharpen the image using the `-unsharp` option. Its arguments are a bit abstruse, but I found [an article on the topic](https://redskiesatnight.com/2005/04/06/sharpening-using-image-magick/) with some good rules of thumb.

### Suffix image filenames with their width and height

```bash
find . -type f -iname "*.png" | \
xargs -L1 magick identify -format "%i\n%d/%t-%wx%h.%e\n" | \
xargs -L2 mv
```
