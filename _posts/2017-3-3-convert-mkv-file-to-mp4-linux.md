---
title:  Convert video and audio files - Linux
layout: post
tags:
  - Linux
  - Linux Commands
---

The `ffmpeg` is a command line tool & we can use that one to convert video & audio files.

### .mkv file to .mp4

	ffmpeg -i input.mkv -codec copy output.mp4

### .mp4 to .avi

ffmpeg -i input.mp4 -codec copy output.avi


[ffmpeg home page](http://ffmpeg.org/){:target="_blank"}
