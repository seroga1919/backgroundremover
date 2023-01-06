# BackgroundRemover

![Background Remover](/examplefiles/backgroundremoverexample.png)
`<img alt="background remover video" src="/examplefiles/backgroundremoverprocessed.gif" height="200" /><br>`

Requirements

* python >= 3.6
* python3.6-dev #or what ever version of python you using
* torch and torchvision stable version (https://pytorch.org)
* ffmpeg 4.4+

#### How to install torch and fmpeg

Go to https://pytorch.org and scroll down to `INSTALL PYTORCH` section and follow the instructions.

For example:

```
PyTorch Build: Stable (1.7.1)
Your OS: Windows
Package: Pip
Language: Python
CUDA: None
```

To install ffmpeg and python-dev

```
sudo apt install ffmpeg python3.6-dev
```

### Installation

To Install backgroundremover, install it from pypi

```bash
pip install --upgrade pip
pip install backgroundremover
```


# Usage as a cli

## Image

Remove the background from a local file image

```bash
backgroundremover -i "/path/to/image.jpeg" -o "output.png"
```

### Advance usage for image background removal

Sometimes it is possible to achieve better results by turning on alpha matting. Example:

```bash
backgroundremover -i "/path/to/image.jpeg" -a -ae 15 -o "output.png"
```

change the model for diferent background removal methods between `u2netp`, `u2net`, or `u2net_human_seg`

```bash
backgroundremover -i "/path/to/image.jpeg" -m "u2net_human_seg" -o "output.png"
```

## Video

### remove background from video and make transparent mov

```bash
backgroundremover -i "/path/to/video.mp4" -tv -o "output.mov"
```

### remove background from local video and overlay it over other video

```bash
backgroundremover -i "/path/to/video.mp4" -tov "/path/to/videtobeoverlayed.mp4" -o "output.mov"
```

### remove background from local video and overlay it over an image

```bash
backgroundremover -i "/path/to/video.mp4" -toi "/path/to/videtobeoverlayed.mp4" -o "output.mov"
```

### remove background from video and make transparent gif

```bash
backgroundremover -i "/path/to/video.mp4" -tg -o "output.gif"
```

### Make matte key file (green screen overlay)

Make a matte file for premier

```bash
backgroundremover -i "/path/to/video.mp4" -mk -o "output.matte.mp4"
```

### Advance usage for video

Change the framerate of the video (default is set to 30)

```bash
backgroundremover -i "/path/to/video.mp4" -fr 30 -tv -o "output.mov"
```

Set total number of frames of the video (default is set to -1, ie the remove background from full video)

```bash
backgroundremover -i "/path/to/video.mp4" -fl 150 -tv -o "output.mov"
```

Change the gpu batch size of the video (default is set to 1)

```bash
backgroundremover -i "/path/to/video.mp4" -gb 4 -tv -o "output.mov"
```

Change the number of workers working on video (default is set to 1)

```bash
backgroundremover -i "/path/to/video.mp4" -wn 4 -tv -o "output.mov"
```

change the model for diferent background removal methods between `u2netp`, `u2net`, or `u2net_human_seg` and limit the frames to 150

```bash
backgroundremover -i "/path/to/video.mp4" -m "u2net_human_seg" -fl 150 -tv -o "output.mov"
```

## Todo

- convert logic from video to image to utilize more GPU on image removal
- clean up documentation a bit more
- add ability to adjust and give feedback images or videos to datasets
- add ability to realtime background removal for videos, for streaming
- finish flask server api
- add ability to use other models than u2net, ie your own.
- other

### Pull requests

Accepted
