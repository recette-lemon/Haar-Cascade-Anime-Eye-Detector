# Haar Cascade Anime Eye Detector 

![ss](https://i.imgur.com/QfFmEWr.png)
![ss](https://i.imgur.com/WtVbkIZ.png)
![ss](https://i.imgur.com/qBeZILC.png)

example:
```python
from PIL import Image, ImageDraw
import numpy
import cv2

cascade = cv2.CascadeClassifier("anime-eyes-cascade.xml")
img = Image.open("pic.png")
array = numpy.array(img)

eyes = cascade.detectMultiScale(
	array,
	scaleFactor=1.1,
	minNeighbors=10,
	minSize=(20, 20),
	flags = cv2.CASCADE_SCALE_IMAGE
)

d = ImageDraw.Draw(img)

for (x, y, w, h) in eyes:
	d.rectangle((x, y, x+w, y+h), outline=(255, 0, 0), width=2)

img.show()
```