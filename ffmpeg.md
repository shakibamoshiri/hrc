# ffmpeg useful Linux commands 


## how to live stream my camera on Linux ?

```bash
ffplay -f v4l2 -framerate 30 -video_size 320x320 /dev/video0
```

