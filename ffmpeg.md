# `ffmpeg` recipes

## Recipes

### Compress a screencast

Full-screen screencasts recorded with QuickTime tend to be on the large size. We can use `ffmpeg` to obtain a smaller size for the file by simply converting it to MP4:

`ffmpeg -i my-recording.mov my-recording.mp4`

### Screencast to GIF

See https://gist.github.com/dergachev/4627207
