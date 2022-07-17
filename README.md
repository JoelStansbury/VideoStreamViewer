# VideoStreamViewer
Widget for ipython environments (e.g. jupyter lab/notebook) for displaying a stream of numpy arrays as a video stream


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
    player.show_frame(frame)
    ret, frame = cap.read()
```
> Note: You'll likely need to utilize `cv2.resize(frame, (h,w))` to scale down the image as the `show_frame` function is quite slow

