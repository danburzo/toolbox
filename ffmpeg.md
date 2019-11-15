# `ffmpeg` recipes

You can find the `ffmpeg` documentation [here](https://ffmpeg.org/ffmpeg.html). I have it installed on macOS with `brew install ffmpeg`.

## Compress a screencast

Full-screen screencasts recorded with QuickTime tend to be on the large side. We can use `ffmpeg` to obtain a smaller file size by simply converting it to MP4:

```bash
ffmpeg -i my-recording.mov my-recording.mp4
```

(For example, it brought a 40-second screencast from 38MB down to 4.5MB)

## Screencast to GIF

There are many ways to turn a video into a GIF with `ffmpeg` and other free tools.

The straightforward way is to:

```bash
ffmpeg -i my-recording.mov -pix_fmt rgb24 output.gif
```

A few useful parameters to include:

* `-r` controls the framerate of the GIF
* `-s` controls the dimensions of the GIF

The example below outputs a 320 &times; 240 GIF with 10 frames per second:

```bash
ffmpeg -i my-recording.mov -pix_fmt rgb24 -r 10 -s 320x240 output.gif
```

However, this method tends to output poorer-quality GIFs. A more complicated solution is explained in this [answer on the Super User StackExchange](https://superuser.com/a/556031), along with an article [detailing how to obtain better-looking GIFs from `ffmpeg`](http://blog.pkh.me/p/21-high-quality-gif-with-ffmpeg.html).

[This gist](https://gist.github.com/dergachev/4627207) walks you through creating a GIF with `ffmpeg` and `gifsicle`.

## Looping a video N times

The `-stream_loop N` option lets you loop (concatenate) the input video N times. In the example below, we generate `output.mp4` which is twenty times the length of `input.mp4`.  

`ffmpeg -stream_loop 20 -i input.mp4 -c copy output.mp4`

> __Note:__ This didn't work with the `ffmpeg` version I had on my machine, so it's best to always keep the program up to date.
