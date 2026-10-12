# Pinnacle Paving – job photo pages

Static page served by GitHub Pages: https://brianpotholepros.github.io/emory-job-photos/

## Add a photo
Resize to ~1200px (card) and ~1600px (`NAME-full.jpg`, used by the tap-to-enlarge lightbox), put both in `img/`, copy an existing photo card in `index.html`.

## Add a video
Compress to 720p H.264 MP4 with faststart (plays inline on iPhone), plus a poster frame:

```sh
mkdir -p video
ffmpeg -i input.mov -vf "scale=-2:720" -c:v libx264 -preset slow -crf 26 -profile:v high -pix_fmt yuv420p \
  -c:a aac -b:a 96k -movflags +faststart video/NAME.mp4
ffmpeg -ss 1 -i video/NAME.mp4 -frames:v 1 -vf "scale=-2:720" -q:v 4 video/NAME-poster.jpg
```

Then copy the commented `VIDEO CARD TEMPLATE` in `index.html` into `<main>`, replace NAME/ADDRESS/details, commit and push. Keep each clip short (under ~50 MB; GitHub rejects files over 100 MB).
