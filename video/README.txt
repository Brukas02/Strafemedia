Drop your scene video files here (skate.mp4, moto.mp4, surf.mp4, rally.mp4).

Re-encode each clip first for smooth scroll scrubbing:
  ffmpeg -i in.mp4 -c:v libx264 -g 1 -crf 20 -pix_fmt yuv420p -movflags +faststart out.mp4

Then in admin.html, set each scene's video path to e.g.:  video/skate.mp4
