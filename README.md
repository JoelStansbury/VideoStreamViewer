# VideoStreamViewer
Widget for ipython environments (e.g. jupyter lab/notebook) for displaying a stream of numpy arrays as a video stream

This sample of code answers the age-old question, "How to display a numpy array as a image?".
This specific approach does so in a way which is suitable for streams of numpy arrays (i.e. a video).

## Requirements
`ipywidgets`: `pip install ipywidgets`
`cv2`: `pip install opencv-python`

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

