# VideoStreamViewer
Widget for ipython environments (e.g. jupyter lab/notebook) for displaying a stream of numpy arrays as a video stream.

This sample of code answers the age-old question, "How to display a numpy array as a image?".
This specific approach does so in a way which is suitable for streams of numpy arrays (i.e. a video).

## When to use it
* When you are manipulating pixel values of frames

## Requirements
`ipywidgets`

## Usage
```python
from array_image import ArrayImage
player = ArrayImage()
player
```
```python
cap = cv2.VideoCapture("soccer.mp4")
ret, frame = cap.read()
while ret:
    frame = cv2.resize(frame, (320, 180))
    player.show_frame(frame[:,:,::-1])
    ret, frame = cap.read()
```
> Note: You'll likely need to utilize `cv2.resize(frame, (h,w))` to scale down the image as the `show_frame` function is quite slow

> Note 2: the `[:,:,::-1]` will swap convert BGR to RGB. This is only because `cv2` loads stuff as BGR by default

## Improvements
If you need a higher framerate, then consider altering the show_frame function to ingest the byte data directly. This would allow you to frontload the processing required to save and re-open the BytesIO file.<br>
You can take this one step further by initializing each frame as an ipywidgets.Image object, then setting `self.children = [new_ImageObj]`, but you'll run into some flickering so I don't rate this option too highly.<br>
You could also just save your array stream as an `.mp4` and then look for a video player widget. Will likely be the fastest option, but I don't know of any video players, I'm just guessing that they exist
