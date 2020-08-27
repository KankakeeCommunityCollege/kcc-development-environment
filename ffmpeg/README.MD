# FFMPEG

> An open-source CLI tool for converting video/audio files to other formats

## Installation

```bash
# long version
brew install ffmpeg

# short version
brew i ffmpeg
```

## Converting MP4 Files to other Formats

### MP4 to OGG/OGV

To convert an MP4 file into an OGV file with OGG audio encoding, use the command below—substituting `<INPUT_FILENAME>.mp4` and `<OUTPUT_FILENAME>.ogg` with your actual mp4's filename and location and the desired output dir and name:

```bash
ffmpeg -i <INPUT_FILENAME>.mp4 -c:v libtheora -q:v 7 -c:a libvorbis -q:a 4 <OUTPUT_FILENAME>.ogv
```

**You can adjust the video and audio quality setting with the `-q:v` and `-q:a` values**. For both the **v**ideo (`-q:v <#>`) and **a**udio (`-q:a <#>`) quality settings, a higher number value creates better quality and bigger file size. Lower values produce reduced video quality and a smaller file size.

**For both audio and video quality settings, replace `<#>` with a number from `0-10`**. _You will have to use trial and error to find the right video/audio quality settings that don't produce massive files_. You're file should generaly not be larger than the original MP4 file.

I focus on one setting first—video, and produce mutliple .ogv files adjusting the video number by 1.

# MP4 to WebM

```bash
ffmpeg -i input.mp4 -c:v libvpx-vp9 -crf 30 -b:v 0 -b:a 128k -c:a libopus output.webm
```
