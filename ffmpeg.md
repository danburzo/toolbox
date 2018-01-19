# `ffmpeg` recipes

## Recipes

### Compress a screencast

Full-screen screencasts recorded with QuickTime tend to be on the large side. We can use `ffmpeg` to obtain a smaller file size by simply converting it to MP4:

`ffmpeg -i my-recording.mov my-recording.mp4`

(For example, it brought a 40-second screencast from 38MB down to 4.5MB)

### Screencast to GIF

See https://gist.github.com/dergachev/4627207
